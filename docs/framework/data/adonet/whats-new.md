---
title: Новые возможности
description: Узнайте о новых возможностях ADO.NET в .NET Framework 4,5, включая новые функции для поставщика данных SqlClient и ADO.NET Entity Framework.
ms.date: 03/30/2017
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
ms.openlocfilehash: b34a27574b6aab75539f9ab30e2978e45b4ad9e3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553861"
---
# <a name="whats-new-in-adonet"></a>Новые возможности в ADO.NET

Следующие функции являются новыми в ADO.NET в .NET Framework 4,5.

## <a name="sqlclient-data-provider"></a>Поставщик данных SqlClient

Следующие функции являются новыми в поставщике .NET Framework данных для SQL Server в .NET Framework 4,5:

- Ключевые слова строки подключения ConnectRetryCount и ConnectRetryInterval (<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>) позволяют управлять возможностью устойчивости бездействующего соединения.

- Поддержка потоковой передачи из SQL Server в приложение поддерживает сценарии, в которых данные на сервере не структурированы.  Дополнительные сведения см. в разделе [Поддержка потоковой передачи SqlClient](sqlclient-streaming-support.md) .

- Добавлена поддержка для асинхронного программирования.  Дополнительные сведения см. в разделе [Асинхронное программирование](asynchronous-programming.md) .

- Ошибки соединения теперь будут отображаться в журнале расширенных событий. Дополнительные сведения см. в разделе [Трассировка данных в ADO.NET](data-tracing.md).

- SqlClient теперь поддерживает функции высокой доступности, аварийного восстановления SQL Server, AlwaysOn. Дополнительные сведения см. в статье [Поддержка SqlClient для обеспечения высокого уровня доступности и аварийного восстановления](./sql/sqlclient-support-for-high-availability-disaster-recovery.md).

- Пароль можно передать в качестве <xref:System.Security.SecureString> при использовании проверки Подлинности SQL Server. Дополнительные сведения см. в разделе <xref:System.Data.SqlClient.SqlCredential>.

- Если `TrustServerCertificate` параметр имеет значение false и `Encrypt` имеет значение true, имя сервера (или IP-адрес) в сертификате SQL Server SSL должно точно совпадать с именем сервера (или IP-адресом), указанным в строке подключения. В противном случае соединение не будет установлено. Дополнительные сведения см. в описании параметра соединения `Encrypt` в <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

  Если это изменение приведет к тому, что в существующем приложении подключение больше не будет устанавливаться, можно внести исправления в приложение с помощью одного из следующих способов.

  - Выпустить сертификат, в котором определяется краткое имя в поле общего имени (CN) или в поле альтернативного имени субъекта (SAN). Это решение применимо для зеркального отображения базы данных.

  - Добавить псевдоним, отображающий краткое имя на полное имя домена.

  - Использовать полное имя домена в строке подключения.

- SqlClient поддерживает расширенную защиту. Дополнительные сведения о расширенной защите см. в разделе [Подключение к ядро СУБД с помощью расширенной защиты](/sql/database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection).

- SqlClient поддерживает соединения с базами данных LocalDB. Дополнительные сведения см. в разделе [Поддержка SqlClient для LocalDB](./sql/sqlclient-support-for-localdb.md).

- `Type System Version=SQL Server 2012;` - это новое значение, которое должно быть передано в свойство соединения `Type System Version`. Значение `Type System Version=Latest;` теперь устарело и заменено эквивалентным `Type System Version=SQL Server 2008;`. Для получения дополнительной информации см. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

- SqlClient обеспечивает дополнительную поддержку разреженных столбцов - средство, которое было добавлено в SQL Server 2008. Если приложение уже имеет доступ к данным в таблице, в которой используется поддержка разреженных столбцов, должно быть обнаружено повышение производительности. Столбец IsColumnSet в <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> указывает, является ли столбец разреженным столбцом, который является элементом набора столбцов. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> Указывает, является ли столбец разреженным (Дополнительные сведения см. в статье [SQL Server коллекции схем](sql-server-schema-collections.md) ). Дополнительные сведения о разреженных столбцах см. в разделе [Использование разреженных столбцов](/sql/relational-databases/tables/use-sparse-columns).

- Сборка Microsoft.SqlServer.Types.dll, содержащая типы пространственных данных, была обновлена с переходом от версии 10.0 к версии 11.0. Работа приложений, которые ссылаются на эту сборку, может оканчиваться сбоем. Дополнительные сведения см. [в разделе критические изменения в ядро СУБДных функциях](/previous-versions/sql/sql-server-2012/ms143179(v=sql.110)).

## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework

.NET Framework 4,5 добавляет API, которые позволяют использовать новые сценарии при работе с Entity Framework 5,0. Дополнительные сведения об улучшениях и функциях, добавленных в Entity Framework 5,0, см. в следующих разделах: [новые](/previous-versions/gg696190(v=vs.103)) и [Entity Framework выпуски и управление версиями](/ef/ef6/what-is-new/past-releases).

## <a name="see-also"></a>См. также

- [ADO.NET](index.md)
- [Общие сведения об ADO.NET](ado-net-overview.md)
- [SQL Server и ADO.NET](./sql/index.md)
- [Новые возможности WCF Data Services 5,0](/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))
