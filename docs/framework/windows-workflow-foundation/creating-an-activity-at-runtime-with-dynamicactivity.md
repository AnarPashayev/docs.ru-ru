---
title: Создание действия в среде выполнения с динамическим действием
description: DynamicActivity — конкретный запечатанный класс с открытым конструктором. Используйте класс для сборки функциональности действий во время выполнения с помощью модели DOM действия.
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 17ee14be7df4801018c7afd2e91f1fb07c34e8e1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421544"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>Создание действия в среде выполнения с динамическим действием
<xref:System.Activities.DynamicActivity> представляет собой конкретный запечатанный класс с открытым конструктором. <xref:System.Activities.DynamicActivity> может использоваться для объединения функций действий во время выполнения с помощью действия DOM.  
  
## <a name="dynamicactivity-features"></a>Возможности DynamicActivity  
 <xref:System.Activities.DynamicActivity> имеет доступ к свойствам, аргументам и переменным выполнения, но не имеет доступа к службам среды выполнения, таким как дочерние действия планирования и отслеживание.  
  
 Значения свойств верхнего уровня можно задавать при помощи объектов рабочих процессов <xref:System.Activities.Argument>. В императивном коде эти аргументы создаются при помощи свойств среды CLR в новом типе. На языке XAML такие аргументы объявляются при помощи тегов `x:Class` и `x:Member`.  
  
 Действия, построенные при помощи интерфейса <xref:System.Activities.DynamicActivity> в конструкторе, использующем <xref:System.ComponentModel.ICustomTypeDescriptor>. Действия, созданные в конструкторе, можно загружать динамически с помощью <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, как показано в следующей процедуре.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Создание действия во время выполнения при помощи императивного кода  
  
1. Опенвисуал Studio 2010.  
  
2. Выберите **файл**, **создать**, **проект**. Выберите **Рабочий процесс 4,0** в разделе **Visual C#** в окне **типы проектов** и выберите узел **v2010** . Выберите в окне **шаблоны** **консольное приложение последовательного рабочего процесса** . Задайте имя для нового проекта DynamicActivitySample.  
  
3. Щелкните правой кнопкой мыши Workflow1. XAML в проекте Хеллоактивити и выберите **Удалить**.  
  
4. Откройте файл Program.cs. Добавьте следующую директиву в начало файла.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. Замените содержимое метода `Main` следующим кодом, который создаст действие <xref:System.Activities.Statements.Sequence>, содержащее отдельное действие <xref:System.Activities.Statements.WriteLine>, и назначит его свойству <xref:System.Activities.DynamicActivity.Implementation%2A> нового динамического действия.  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6. Запустите приложение. Окно консоли с текстом "Hello World!" Отображает.  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>Создание действия во время выполнения при помощи языка XAML  
  
1. Откройте Visual Studio 2010.  
  
2. Выберите **файл**, **создать**, **проект**. Выберите **Рабочий процесс 4,0** в разделе **Visual C#** в окне **типы проектов** и выберите узел **v2010** . Выберите **консольное приложение рабочего процесса** в окне **шаблоны** . Задайте имя для нового проекта DynamicActivitySample.  
  
3. Откройте файл Workflow1.xaml в проекте HelloActivity. Щелкните параметр **arguments (аргументы** ) в нижней части конструктора. Создайте новый аргумент `In`, вызываемый методом `TextToWrite` типа `String`.  
  
4. Перетащите действие **WriteLine** из раздела **примитивы** области элементов на поверхность конструктора. Присвойте значение `TextToWrite` свойству **Text** действия.  
  
5. Откройте файл Program.cs. Добавьте следующую директиву в начало файла.  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. Замените содержимое метода `Main` следующим кодом.  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. Запустите приложение. Окно консоли с текстом "Hello World!" Появится .  
  
8. Щелкните правой кнопкой мыши файл Workflow1. XAML в **Обозреватель решений** и выберите команду **Просмотреть код**. Следует отметить, что класс действия создается при помощи `x:Class`, а свойство - при помощи `x:Property`.  
  
## <a name="see-also"></a>Дополнительно

- [Разработка рабочих процессов, действий и выражений с помощью императивного кода](authoring-workflows-activities-and-expressions-using-imperative-code.md)
