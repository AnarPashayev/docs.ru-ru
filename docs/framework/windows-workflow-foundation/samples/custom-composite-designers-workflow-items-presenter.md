---
title: Пользовательские составные конструкторы - средство представления элементов рабочего процесса
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: f4db3325081a820a37a8791849d2ad9697d15151
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118109"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a>Пользовательские составные конструкторы - средство представления элементов рабочего процесса
<xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> является типом ключа в модели программирования конструктора WF, позволяющим редактирование коллекции содержащихся элементов. В этом образце показано, как построить конструктор действий, который предоставляет доступ к такой изменяемой коллекции.

 В этом образце показаны следующие действия.

-   Создание настраиваемого конструктора действий с <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.

-   Создание конструктора действий со «свернутым» и «развернутым» представлением.

-   Переопределение конструктора по умолчанию в повторно размещенном приложении.

### <a name="to-set-up-build-and-run-the-sample"></a>Настройка, сборка и выполнение образца

1.  Откройте **UsingWorkflowItemsPresenter.sln** образец решения для C# или VB в Visual Studio 2010.

2.  Постройте и запустите это решение. Должно открыться повторно размещенное приложение конструктора рабочих процессов, после чего действия можно перетащить на полотно.

## <a name="sample-highlights"></a>Описание образца
 Код для этого образца показывает следующее.

-   Для создания действия конструктора:  `Parallel`

-   Создание настраиваемого конструктора действий с <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>. Некоторые замечания.

    -   Обратите внимание на использование привязки данных WPF для привязки к `ModelItem.Branches`. `ModelItem` Свойство `WorkflowElementDesigner` , относится к базовому объекту которого используется конструктор, в этом случае наш `Parallel`.

    -   Шаблон <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> может использоваться для указания видимого изображения, отображаемого между отдельными элементами коллекции.

    -   <xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> — Это шаблон, который можно предоставить для определения макета элементов в коллекции. В данном случае используется горизонтальный элемент StackPanel.

 Это показано в следующем примере кода.

```xaml
<sad:WorkflowItemsPresenter HintText="Drop Activities Here"
                              Items="{Binding Path=ModelItem.Branches}">
    <sad:WorkflowItemsPresenter.SpacerTemplate>
      <DataTemplate>
        <Ellipse Width="10" Height="10" Fill="Black"/>
      </DataTemplate>
    </sad:WorkflowItemsPresenter.SpacerTemplate>
    <sad:WorkflowItemsPresenter.ItemsPanel>
      <ItemsPanelTemplate>
        <StackPanel Orientation="Horizontal"/>
      </ItemsPanelTemplate>
    </sad:WorkflowItemsPresenter.ItemsPanel>
  </sad:WorkflowItemsPresenter>
```

-   Выполнение связи объекта `DesignerAttribute` с типом `Parallel`, а затем вывод указанных атрибутов.

    -   Сначала зарегистрируйте все конструкторы по умолчанию.

 Ниже приведен пример кода.

```csharp
// register metadata
(new DesignerMetadata()).Register();
RegisterCustomMetadata();
```

```vb
' register metadata
Dim metadata = New DesignerMetadata()
metadata.Register()
' register custom metadata
RegisterCustomMetadata()
```

    -   Далее переопределите параллель в методе `RegisterCustomMetadata`.

 В следующем коде это показано на языках C# и Visual Basic.

```csharp
void RegisterCustomMetadata()
{
      AttributeTableBuilder builder = new AttributeTableBuilder();
      builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
      MetadataStore.AddAttributeTable(builder.CreateTable());
}
```

```vb
Sub RegisterCustomMetadata()
   Dim builder As New AttributeTableBuilder()
   builder.AddCustomAttributes(GetType(Parallel), New DesignerAttribute(GetType(CustomParallelDesigner)))
   MetadataStore.AddAttributeTable(builder.CreateTable())
End Sub
```

-   Наконец, обратите внимание на использование различных шаблонов данных и триггеров для выбора соответствующего шаблона на основании свойства `IsRootDesigner`.

 Ниже приведен пример кода.

```xaml
<sad:ActivityDesigner x:Class="Microsoft.Samples.CustomParallelDesigner"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:sad="clr-namespace:System.Activities.Design;assembly=System.Activities.Design"
    xmlns:sadv="clr-namespace:System.Activities.Design.View;assembly=System.Activities.Design">
  <sad:ActivityDesigner.Resources>
    <DataTemplate x:Key="Expanded">
      <StackPanel>
        <TextBlock>This is the Expanded View</TextBlock>
        <sad:WorkflowItemsPresenter HintText="Drop Activities Here"
                                    Items="{Binding Path=ModelItem.Branches}">
          <sad:WorkflowItemsPresenter.SpacerTemplate>
            <DataTemplate>
              <Ellipse Width="10" Height="10" Fill="Black"/>
            </DataTemplate>
          </sad:WorkflowItemsPresenter.SpacerTemplate>
          <sad:WorkflowItemsPresenter.ItemsPanel>
            <ItemsPanelTemplate>
              <StackPanel Orientation="Horizontal"/>
            </ItemsPanelTemplate>
          </sad:WorkflowItemsPresenter.ItemsPanel>
        </sad:WorkflowItemsPresenter>
      </StackPanel>
    </DataTemplate>
    <DataTemplate x:Key="Collapsed">
      <TextBlock>This is the Collapsed View</TextBlock>
    </DataTemplate>
    <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
      <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
      <Style.Triggers>
        <DataTrigger Binding="{Binding Path=IsRootDesigner}" Value="true">
          <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
        </DataTrigger>
      </Style.Triggers>
    </Style>
  </sad: ActivityDesigner.Resources>
  <Grid>
    <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>
  </Grid>
</sad: ActivityDesigner>
```

> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры. Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`  
  
## <a name="see-also"></a>См. также

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [Разработка приложений с помощью конструктора рабочего процесса](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
