---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: b5f2dbb687348afac98247cb21bae831dea26bfe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183316"
---
# <a name="dbproviderfactories"></a>DbProviderFactories

Пространство имен <xref:System.Data.Common> предоставляет классы для создания экземпляров <xref:System.Data.Common.DbProviderFactory> для работы с конкретными источниками данных. При создании экземпляра <xref:System.Data.Common.DbProviderFactory> и передаче ему сведений о поставщике данных фабрика `DbProviderFactory` может на их основе определить верный, строго типизированный объект соединения, который необходимо возвратить.  
  
 Начиная с версии 4 платформы .NET Framework, такие поставщики данных, как <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient> и <xref:System.Data.OracleClient>, больше не перечисляются в файле machine.config, однако настраиваемые поставщики будут по-прежнему перечислены там.  
  
## <a name="in-this-section"></a>в этом разделе  

 [Общие сведения о модели фабрики](factory-model-overview.md)  
 Содержит общие сведения о шаблоне разработки и программном интерфейсе фабрики.  
  
 [Получение класса DbProviderFactory](obtaining-a-dbproviderfactory.md)  
 Показывает способ создания списка установленных поставщиков данных и соединения <xref:System.Data.Common.DbConnection> в фабрике `DbProviderFactory`.  
  
 [DbConnection, DbCommand и DbException](dbconnection-dbcommand-and-dbexception.md)  
 Показывает способ создания объектов <xref:System.Data.Common.DbCommand> и <xref:System.Data.Common.DbDataReader>, а также методы обработки ошибок с помощью исключения <xref:System.Data.Common.DbException>.  
  
 [Изменение данных с помощью DbDataAdapter](modifying-data-with-a-dbdataadapter.md)  
 Показывает способ использования объектов <xref:System.Data.Common.DbCommandBuilder> совместно с <xref:System.Data.Common.DbDataAdapter> для получения и изменения данных.  
  
## <a name="see-also"></a>См. также раздел

- [Извлечение и изменение данных в ADO.NET](retrieving-and-modifying-data.md)
- [Общие сведения об ADO.NET](ado-net-overview.md)
