---
title: Обработка событий DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: 6c2e554b7e6bde3e82190f70723f272b0d39a18a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152416"
---
# <a name="handling-dataview-events"></a>Обработка событий DataView
Событие <xref:System.Data.DataView.ListChanged> объекта <xref:System.Data.DataView> используется для определения того, было ли обновлено представление. К обновлениям, которые вызывают это событие, относятся добавление, удаление или изменение строки в базовой таблице, добавление или удаление столбца из схемы базовой таблицы, изменение в родительской или дочерней связи. **ListChanged** событий также уведомляет вас, когда список строк, которые вы просматриваете значительно изменен из-за применения нового порядка сортировки или фильтра.  
  
 **ListChanged** реализует событие **ListChangedEventHandler** делегата <xref:System.ComponentModel> пространства имен и принимает в качестве ввода <xref:System.ComponentModel.ListChangedEventArgs> объекта. Можно определить, какие изменения фиксируется с помощью <xref:System.ComponentModel.ListChangedType> значение перечисления в **ListChangedType** свойство **ListChangedEventArgs** объекта. Для изменения, которые включают добавление, удаление или перемещение строк, новому индексу добавленной или перемещенной строки и к прежнему индексу удаленной строки может осуществляться с использованием **NewIndex** свойство **ListChangedEventArgs** объекта. В случае перемещение строки, к прежнему индексу перемещенной строки можно получить, используя **OldIndex** свойство **ListChangedEventArgs** объекта.  
  
 **DataViewManager** также предоставляет **ListChanged** для оповещения о том, если таблицы были добавлены или удалены, или в том случае, если был изменен для **отношений** коллекцию базовый **набора данных**.  
  
 В следующем примере кода показано, как добавить **ListChanged** обработчик событий.  
  
```vb  
AddHandler custView.ListChanged, _  
  New System.ComponentModel.ListChangedEventHandler( _  
  AddressOf OnListChanged)  
  
Private Shared Sub OnListChanged( _  
  sender As Object, args As System.ComponentModel.ListChangedEventArgs)  
  Console.WriteLine("ListChanged:")  
  Console.WriteLine(vbTab & "    Type = " & _  
    System.Enum.GetName(args.ListChangedType.GetType(), _  
    args.ListChangedType))  
  Console.WriteLine(vbTab & "OldIndex = " & args.OldIndex)  
  Console.WriteLine(vbTab & "NewIndex = " & args.NewIndex)  
End Sub  
```  
  
```csharp  
custView.ListChanged  += new   
  System.ComponentModel.ListChangedEventHandler(OnListChanged);  
  
protected static void OnListChanged(object sender,   
  System.ComponentModel.ListChangedEventArgs args)  
{  
  Console.WriteLine("ListChanged:");  
  Console.WriteLine("\t    Type = " + args.ListChangedType);  
  Console.WriteLine("\tOldIndex = " + args.OldIndex);  
  Console.WriteLine("\tNewIndex = " + args.NewIndex);  
}  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [Объекты DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [Управляемые поставщики ADO.NET и центр разработчиков DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
