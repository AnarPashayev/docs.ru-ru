---
title: Разработка действий рабочих процессов с помощью класса CodeActivity
ms.date: 03/30/2017
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
ms.openlocfilehash: 549acec8b8101312d48bd20e63a4a988b798ff38
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767400"
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a>Разработка действий рабочих процессов с помощью класса CodeActivity
Действия, созданные путем наследования от <xref:System.Activities.CodeActivity>, могут реализовывать базовое императивное поведение путем переопределения метода <xref:System.Activities.CodeActivity.Execute%2A>.

## <a name="using-codeactivitycontext"></a>Использование CodeActivityContext
 Доступ к функциям среды выполнения рабочего процесса можно получить из метода <xref:System.Activities.CodeActivity.Execute%2A> при помощи элементов параметра `context` типа <xref:System.Activities.CodeActivityContext>. Функции, доступные посредством <xref:System.Activities.CodeActivityContext>:

-   Возврат и задание значений аргументов и переменных.

-   Пользовательские функции отслеживания с использованием <xref:System.Activities.CodeActivityContext.Track%2A>.

-   Доступ к свойствам выполнения действия с помощью <xref:System.Activities.CodeActivityContext.GetProperty%2A>.

#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a>Создание настраиваемого действия, которое наследуется от CodeActivity

1. Откройте Visual Studio 2010.

2. Выберите **файл**, **новый**, а затем **проекта**. Выберите **Workflow 4.0** под **Visual C#** в **типы проектов** затем выберите **v2010** узла. Выберите **библиотеки действий** в **шаблоны** окна. Задайте имя для нового проекта HelloActivity.

3. Щелкните правой кнопкой мыши Activity1.xaml в проекте HelloActivity и выберите **удалить**.

4. Щелкните правой кнопкой мыши проект HelloActivity и выберите **добавить** , а затем **класс**. Задайте имя для нового класса HelloActivity.cs.

5. В файле HelloActivity.cs добавьте следующие директивы `using`.

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. Сделайте так, чтобы новый класс наследовал от действия <xref:System.Activities.CodeActivity> путем добавления базового класса к объявлению класса.

    ```csharp
    class HelloActivity : CodeActivity
    ```

7. Добавьте функциональные возможности к классу путем добавления метода <xref:System.Activities.CodeActivity.Execute%2A>.

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. Используйте объект <xref:System.Activities.CodeActivityContext> для создания записи отслеживания.

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));
        context.Track(record);
    }
    ```
