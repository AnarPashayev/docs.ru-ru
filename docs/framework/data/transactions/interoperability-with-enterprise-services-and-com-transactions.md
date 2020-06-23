---
title: Взаимодействие с транзакциями Enterprise Services и COM+
description: Общие сведения о взаимодействии с корпоративными службами и транзакциями COM+ в .NET с помощью пространства имен System. Transactions.
ms.date: 03/30/2017
ms.assetid: d0fd0d26-fe86-443b-b208-4d57d39fa4aa
ms.openlocfilehash: ebd6166fbd99ef102cf10ba1bcef9e3eb8aaa5da
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141905"
---
# <a name="interoperability-with-enterprise-services-and-com-transactions"></a>Взаимодействие с транзакциями Enterprise Services и COM+
Пространство имен <xref:System.Transactions> поддерживает взаимодействие между объектами транзакций, созданными с помощью этого пространства имен, и транзакциями, созданными с помощью модели COM+.  
  
 Чтобы задать уровень взаимодействия с транзакциями COM+ при создании нового экземпляра <xref:System.Transactions.EnterpriseServicesInteropOption>, можно использовать перечисление <xref:System.Transactions.TransactionScope>.  
  
 По умолчанию, когда код приложения проверяет статическое <xref:System.Transactions.Transaction.Current%2A> свойство, <xref:System.Transactions> пытается найти транзакцию, которая в противном случае является текущей, или <xref:System.Transactions.TransactionScope> объект, который определяет, что <xref:System.Transactions.Transaction.Current%2A> имеет **значение NULL**. Если ни один из этих элементов не найден, <xref:System.Transactions> запрашивает транзакцию в контексте COM+. Обратите внимание, что даже если инфраструктура <xref:System.Transactions> находит транзакцию в контексте COM+, она по-прежнему отдает предпочтение транзакциям, присущим инфраструктуре <xref:System.Transactions>.  
  
## <a name="interoperability-levels"></a>Уровни взаимодействия  
 Перечисление <xref:System.Transactions.EnterpriseServicesInteropOption> определяет следующие уровни взаимодействия: <xref:System.Transactions.EnterpriseServicesInteropOption.None>, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> и <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>.  
  
 Класс <xref:System.Transactions.TransactionScope> предоставляет конструкторы, принимающие перечисление <xref:System.Transactions.EnterpriseServicesInteropOption> в качестве параметра.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.None>, как подразумевает имя, подразумевает отсутствие взаимодействия между <xref:System.EnterpriseServices> контекстами и областями транзакций. После создания объекта <xref:System.Transactions.TransactionScope> со значением <xref:System.Transactions.EnterpriseServicesInteropOption.None> никакие изменения свойства <xref:System.Transactions.Transaction.Current%2A> не отражаются в контексте COM+. Аналогичным образом, изменения транзакции в контексте COM+ не отражаются в свойстве <xref:System.Transactions.Transaction.Current%2A>. Это самый быстрый режим работы <xref:System.Transactions>, поскольку никакая дополнительная синхронизация не требуется. <xref:System.Transactions.EnterpriseServicesInteropOption.None> - это значение по умолчанию, используемое объектом <xref:System.Transactions.TransactionScope> со всеми конструкторами, не принимающими <xref:System.Transactions.EnterpriseServicesInteropOption> в качестве параметра.  
  
 Чтобы объединить транзакции <xref:System.EnterpriseServices> с внешней транзакцией, необходимо использовать значение <xref:System.Transactions.EnterpriseServicesInteropOption.Full> или <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>. Оба этих значения основываются на функции "бескомпонентные службы", поэтому их использование возможно на компьютерах под управлением операционных систем Windows XP с пакетом обновления 2 (SP2) или Windows Server 2003.  
  
 Значение <xref:System.Transactions.EnterpriseServicesInteropOption.Full> указывает, что внешние транзакции для <xref:System.Transactions> и <xref:System.EnterpriseServices> всегда одинаковы. В результате создается новый транзакционный контекст <xref:System.EnterpriseServices>, и транзакция, являющаяся текущей для объекта <xref:System.Transactions.TransactionScope>, становится текущей для этого контекста. Транзакция в <xref:System.Transactions.Transaction.Current%2A> полностью синхронизирована с транзакцией в <xref:System.EnterpriseServices.ContextUtil.Transaction%2A>. Использование данного значения приводит к снижению производительности, поскольку может потребоваться создание новых контекстов COM+.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>задает следующие требования.  
  
- При проверке свойства <xref:System.Transactions.Transaction.Current%2A> инфраструктура <xref:System.Transactions> должна поддерживать транзакции в контексте COM+, если обнаруживается, что данный объект выполняется в контексте, отличном от контекста по умолчанию. Обратите внимание, что транзакция не может содержаться в контексте по умолчанию. Таким образом, в контексте по умолчанию для свойства <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic> возвращается транзакция, которая хранится в локальной памяти потока, используемой инфраструктурой <xref:System.Transactions>, даже если задано значение <xref:System.Transactions.Transaction.Current%2A>.  
  
- Если создание нового объекта <xref:System.Transactions.TransactionScope> происходит в контексте, отличном от контекста по умолчанию, транзакция, являющаяся текущей для объекта <xref:System.Transactions.TransactionScope>, должна быть отражена в контексте COM+. В этом случае использование значения <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic> приводит к тому же самому результату, что и при использовании значения <xref:System.Transactions.EnterpriseServicesInteropOption.Full> - создается контекст COM+.  
  
 Кроме того, если для свойства <xref:System.Transactions.Transaction.Current%2A> определено как значение <xref:System.Transactions.EnterpriseServicesInteropOption.Full>, так и значение <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>, оба этих режима подразумевают, что свойство <xref:System.Transactions.Transaction.Current%2A> нельзя задать напрямую.  Любая попытка задать свойство <xref:System.Transactions.Transaction.Current%2A> напрямую без создания объекта <xref:System.Transactions.TransactionScope> приводит к возникновению исключения <xref:System.InvalidOperationException>. Значение перечисления <xref:System.Transactions.EnterpriseServicesInteropOption> наследуется новыми областями транзакций, в которых явно не указано, какое значение следует использовать. Например, если создать новый объект <xref:System.Transactions.TransactionScope> со значением <xref:System.Transactions.EnterpriseServicesInteropOption.Full>, а затем создать второй объект <xref:System.Transactions.TransactionScope> без указания значения перечисления <xref:System.Transactions.EnterpriseServicesInteropOption>, второй объект <xref:System.Transactions.TransactionScope> будет также иметь значение <xref:System.Transactions.EnterpriseServicesInteropOption.Full>.  
  
 При создании новой области транзакции применяются следующие правила:  
  
1. <xref:System.Transactions.Transaction.Current%2A>проверяет наличие транзакции. Эта проверка заключается в выполнении следующих действий.  
  
    - Проверяется существование области.  
  
    - Если область существует, проверяется значение перечисления <xref:System.Transactions.EnterpriseServicesInteropOption>, переданное при создании области.  
  
    - Если значением перечисления <xref:System.Transactions.EnterpriseServicesInteropOption> является <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>, транзакция COM+ (транзакция <xref:System.EnterpriseServices>) имеет приоритет над транзакцией <xref:System.Transactions> в локальной памяти управляемого потока.  
  
         В случае значения <xref:System.Transactions.EnterpriseServicesInteropOption.None> приоритет имеет транзакция <xref:System.Transactions> в локальной памяти управляемого потока.  
  
         В случае значения <xref:System.Transactions.EnterpriseServicesInteropOption.Full> существует только одна транзакция - транзакция COM+.  
  
2. Проверяется значение перечисления <xref:System.Transactions.TransactionScopeOption>, переданное конструктором <xref:System.Transactions.TransactionScope>. Это позволяет определить необходимость создания новой транзакции.  
  
3. Если необходимо создать новую транзакцию, в зависимости от желаемого результата используются различные значения перечисления <xref:System.Transactions.EnterpriseServicesInteropOption>.  
  
    - <xref:System.Transactions.EnterpriseServicesInteropOption.Full>: позволяет создать транзакцию, связанную с контекстом COM+.  
  
    - <xref:System.Transactions.EnterpriseServicesInteropOption.None>: <xref:System.Transactions> транзакция создана.  
  
    - <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>. Если контекст COM+ существует, транзакция создается и прикрепляется к контексту.  
  
 В следующей таблице представлены контекст Enterprise Services (ES) и область транзакции, запрашивающая транзакцию с помощью перечисления <xref:System.Transactions.EnterpriseServicesInteropOption>.  
  
|Контекст ES|None|Автоматический|Полное|  
|----------------|----------|---------------|----------|  
|Контекст по умолчанию|Контекст по умолчанию|Контекст по умолчанию|Create new <br />транзакционный контекст|  
|Контекст, отличный от контекста по умолчанию|Сохранить контекст клиента|Создать новый транзакционный контекст|Создать новый транзакционный контекст|  
  
 В следующей таблице показано, что представляют собой внешняя транзакция в случае конкретного контекста <xref:System.EnterpriseServices> и область транзакции, запрашивающая транзакцию с помощью перечисления <xref:System.Transactions.EnterpriseServicesInteropOption>.  
  
|Контекст ES|None|Автоматический|Полное|  
|----------------|----------|---------------|----------|  
|Контекст по умолчанию|ST|ST|ES|  
|Контекст, отличный от контекста по умолчанию|ST|ES|ES|  
  
 В приведенной выше таблице:  
  
- ST означает, что управление внешней транзакцией области осуществляется инфраструктурой <xref:System.Transactions> отдельно от любой существующей транзакции контекста <xref:System.EnterpriseServices>;  
  
- ES означает, что внешняя транзакция области совпадает с транзакцией контекста <xref:System.EnterpriseServices>.
