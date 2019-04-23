---
title: Использование инфраструктуры System.Transactions в среде ASP.NET
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: df9a9f1878b2268d1d6bc3d9b05d0ad8d7bcc3f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134598"
---
# <a name="using-systemtransactions-in-aspnet"></a>Использование инфраструктуры System.Transactions в среде ASP.NET
В этом разделе описывается, как можно эффективно использовать пространство имен <xref:System.Transactions> в приложении [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] .  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a>Включение разрешения DistributedTransactionPermission в ASP.NET  
 <xref:System.Transactions> поддерживает частично доверенных вызывающих и отмечена атрибутом **AllowPartiallyTrustedCallers** (APTCA). Уровни доверия для сборки <xref:System.Transactions> определяются на основе типов ресурсов (например, системная память, ресурсы, общие для всего процесса, ресурсы, общие для всей системы, и другие ресурсы), которые используются в <xref:System.Transactions> , и уровня доверия, необходимого для доступа к этим ресурсам. В среде с частичным доверием сборка с неполным доверием может использовать только транзакции внутри домена приложения (в этом случае единственным защищаемым ресурсом является системная память), пока этой сборке не будет предоставлено разрешение <xref:System.Transactions.DistributedTransactionPermission>.  
  
 Разрешение<xref:System.Transactions.DistributedTransactionPermission> запрашивается при каждой передаче управления транзакцией координатору распределенных транзакций (Майкрософт) (MSDTC). В этом сценарии используются ресурсы, общие для всего процесса, и прежде всего один глобальный ресурс, зарезервированный в журнале MSDTC, например внешнее веб-приложение для взаимодействия с базой данных или приложение, использующее базу данных в рамках предоставляемых им служб.  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] имеет собственный набор уровней доверия, с которыми при помощи файлов политики связан определенный набор разрешений. Дополнительные сведения см. в разделе [уровни доверия в ASP.NET и файлы политики](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)). После первоначальной установки пакета Windows SDK ни один из файлов политики [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] по умолчанию не связан с разрешением <xref:System.Transactions.DistributedTransactionPermission>. Поэтому передачу управления транзакцией приложения [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] координатору MSDTC выполнить не удается: возникает исключение <xref:System.Security.SecurityException> при запросе разрешения <xref:System.Transactions.DistributedTransactionPermission>. Чтобы обеспечить передачу транзакции на следующий уровень иерархии среды [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] с частичным уровнем доверия, необходимо предоставить разрешение <xref:System.Transactions.DistributedTransactionPermission> для уровней доверия по умолчанию, у которых есть разрешение <xref:System.Data.SqlClient.SqlClientPermission>. Можно настроить пользовательский уровень доверия и файл политики для его поддержки или изменить файлы политики по умолчанию **Web_hightrust.config** и **Web_mediumtrust.config**.  
  
 Чтобы изменить файлы политики, добавьте **SecurityClass** элемент для **DistributedTransactionPermission** для **SecurityClasses** элемента под  **PolicyLevel** элемент и добавьте соответствующий **IPermission** элемента под [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** для System.Transactions. Это показано в следующем файле конфигурации.  
  
```xml  
<SecurityClasses>  
   <SecurityClass Name="DistributedTransactionPermission" Description="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
...  
</SecurityClasses>  
  
<PermissionSet  
  class="NamedPermissionSet"  
  version="1"  
  Name="ASP.Net">  
     <IPermission  
        class="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
        version="1"  
        Unrestricted="true"  
     />  
...  
</PermissionSet>  
```  
  
 Дополнительные сведения о [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] политику безопасности, см. в разделе [элемент securityPolicy (схема параметров ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).  
  
## <a name="dynamic-compilation"></a>Динамическая компиляция  
 Чтобы импортировать и использовать <xref:System.Transactions> в приложении [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] , динамически компилируемом во время доступа, в файле конфигурации необходимо указать ссылку на сборку <xref:System.Transactions> . В частности, ссылку необходимо добавить в раздел **compilation**/**assemblies** корневого файла конфигурации по умолчанию **Web.config** или файла конфигурации конкретного веб-приложения. В следующем примере это показано.  
  
```xml  
<configuration>  
   <system.web>  
      <compilation>  
         <assemblies>  
      <add assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
         </assemblies>  
      </compilation>  
   </system.web>  
</configuration>  
```  
  
 Дополнительные сведения см. в разделе [элемент add для сборки для компиляции (схема параметров ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).  
  
## <a name="see-also"></a>См. также

- [Уровни доверия в ASP.NET и файлы политики](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))
- [Элемент securityPolicy (схема параметров ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))
- [Передача управления транзакцией на следующий уровень иерархии](../../../../docs/framework/data/transactions/transaction-management-escalation.md)
