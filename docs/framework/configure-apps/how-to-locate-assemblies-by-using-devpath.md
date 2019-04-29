---
title: Практическое руководство. Поиск сборок с помощью DEVPATH
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 5c4041f42b0a9d1d1e4bc8438e662911534daa42
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775834"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>Практическое руководство. Поиск сборок с помощью DEVPATH
Разработчикам может потребоваться, общая сборка, которую они создадут правильно работает с несколькими приложениями. Вместо постоянно помещать сборку в глобальный кэш сборок во время цикла разработки, разработчик может создать переменной среды DEVPATH, которая указывает выходной каталог сборки для сборки.  
  
 Например предположим, что вы создаете вызывается MySharedAssembly общей сборки и в выходной каталог C:\MySharedAssembly\Debug. C:\MySharedAssembly\Debug можно поместить в переменную DEVPATH. Необходимо указать [ \<developmentMode >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) элемент в файле конфигурации компьютера. Этот элемент указывает среда CLR нужно использовать DEVPATH для поиска сборок.  
  
 Общая сборка должна быть обнаруживаема среды выполнения.  Для указания закрытого каталога для разрешения использования ссылок на сборки [ \<codeBase > элемент](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) или [ \<probing > элемент](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) в файле конфигурации, как описано в разделе [Указание расположения сборки](../../../docs/framework/configure-apps/specify-assembly-location.md).  Можно также поместить сборку в подкаталоге каталога приложения. Дополнительные сведения см. в разделе [Обнаружение сборок в среде выполнения](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
> [!NOTE]
>  Это расширенная функция, предназначенная только для разработки.  
  
 В следующем примере показано, как среда выполнения для поиска сборок в каталогах, указанных в переменной среды DEVPATH.  
  
## <a name="example"></a>Пример  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 Этот параметр по умолчанию false.  
  
> [!NOTE]
>  Используйте этот параметр только во время разработки. Среда выполнения не проверяет версии на в DEVPATH сборок со строгим именем. Он просто использует первый найденную сборку.  
  
## <a name="see-also"></a>См. также

- [Настройка приложений с помощью файлов конфигурации](index.md)
