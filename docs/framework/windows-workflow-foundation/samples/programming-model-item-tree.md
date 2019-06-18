---
title: Программирование дерева элементов модели
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: 59c1f0c3722d6e68a9f629504f5012377dbacc5f
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170072"
---
# <a name="programming-model-item-tree"></a>Программирование дерева элементов модели
В этом примере демонстрируется переход <xref:System.Activities.Presentation.Model.ModelItem> дерева, используя привязку декларативных данных из представления дерева Windows Presentation Foundation (WPF).

## <a name="sample-details"></a>Подробные сведения об образце
 Дерево <xref:System.Activities.Presentation.Model.ModelItem> является абстракцией, которая используется инфраструктурой [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] для предоставления данных о базовом изменяемом экземпляре. На следующей иллюстрации показаны различные слои инфраструктуры внутри [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].

 ![Схема, показывающая архитектура конструктора рабочих процессов.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 Элемент <xref:System.Activities.Presentation.Model.ModelItem> состоит из указателя базового значения, а также коллекции объектов <xref:System.Activities.Presentation.Model.ModelProperty>. Объект <xref:System.Activities.Presentation.Model.ModelProperty> в свою очередь включает данные, такие как имя и тип свойства, и указатель значения, который в свою очередь является еще одним элементом <xref:System.Activities.Presentation.Model.ModelItem>. Преобразователь значений используется для манипуляции некоторыми элементами <xref:System.Activities.Presentation.Model.ModelItem>, возвращаемыми свойством <xref:System.Activities.Presentation.Model.ModelProperty>, чтобы они правильно отображались в представлении дерева. Далее в образце показано, как императивно программировать с использованием дерева <xref:System.Activities.Presentation.Model.ModelItem> при помощи императивных инструкций, в соответствии со следующим примером.

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a>Использование этого образца

1. Откройте решение ProgrammingModelItemTree.sln в Visual Studio 2010.

2. Постройте решение, выбрав **построить решение** из **построения** меню.

3. Нажмите клавишу F5 для запуска приложения. Затем отображается форма WPF.

4. Нажмите кнопку **загрузить WF** кнопку, чтобы загрузить <xref:System.Activities.Presentation.Model.ModelItem> и привязать его к представлении в виде дерева.

5. Щелкнув **изменить дерево элементов модели** кнопки выполняется предшествующий код, чтобы добавить элемент в дерево и задает свойство.

> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры. Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.Data.IValueConverter>
