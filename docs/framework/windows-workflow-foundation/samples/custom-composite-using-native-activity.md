---
title: Пользовательское составное действие, использующее собственное действие
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 41a823ab00a2be0772a07b15d1292dbb4e8d1a6b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59340299"
---
# <a name="custom-composite-using-native-activity"></a>Пользовательское составное действие, использующее собственное действие
В этом образце показано, как разработать действие <xref:System.Activities.NativeActivity>, которое планирует другие объекты <xref:System.Activities.Activity> для управления потоком выполнения рабочего процесса. В этом образце используются два общих потока управления, Sequence и While, для демонстрации того, как это сделать.

## <a name="sample-details"></a>Подробные сведения об образце
 Прежде всего об объекте `MySequence` следует отметить, что он является производным от <xref:System.Activities.NativeActivity>. <xref:System.Activities.NativeActivity> — <xref:System.Activities.Activity> объекта, который предоставляет доступ ко всем возможностям среды выполнения рабочего процесса с помощью <xref:System.Activities.NativeActivityContext> передается `Execute` метод.

 `MySequence` предоставляет доступ к общедоступной коллекции <xref:System.Activities.Activity> объектов, которая заполняется разработчиком рабочего процесса. Перед выполнением рабочего процесса среда выполнения рабочего процесса вызывает метод <xref:System.Activities.Activity.CacheMetadata%2A> для каждого действия в рабочем процессе. В ходе этого процесса среда выполнения определяет связи типа «родитель-потомок» в целях управления областью определения данных и временем существования. Реализация по умолчанию <xref:System.Activities.Activity.CacheMetadata%2A> использует метод <xref:System.ComponentModel.TypeDescriptor> класс для экземпляра `MySequence` действия для добавления любого общедоступного свойства типа <xref:System.Activities.Activity> или <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Activity>> как дочерние элементы `MySequence` действия.

 Каждый раз, когда действие предоставляет доступ к общедоступной коллекции дочерних действий, возникает вероятность того, что эти дочерние действия будут приобретать одинаковое состояние. Рекомендуется, чтобы родительское действие, в данном случае `MySequence`, также предоставляло доступ к коллекции переменных, с помощью которых дочерние действия могли бы это осуществить. Аналогии с дочерними действиями <xref:System.Activities.Activity.CacheMetadata%2A> метод добавляет общедоступные свойства типа <xref:System.Activities.Variable> или <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Variable>> как переменные, связанные с `MySequence` действия.

 Помимо общедоступных переменных, которыми управляют действия, дочерние по отношению к `MySequence`, действие `MySequence` должно также следить, где оно находится с точки зрения выполнения его дочерних действий. Для этого в нем используется закрытая переменная `currentIndex`. Эта переменная регистрируется как часть среды `MySequence` путем добавления вызова метода <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> в метод `MySequence` действия <xref:System.Activities.Activity.CacheMetadata%2A>. Объекты <xref:System.Activities.Activity>, добавленные в коллекцию `MySequence` `Activities`, не могут получить доступ к переменным, добавленным таким образом.

 При выполнении средой выполнения действия `MySequence` она вызывает его метод <xref:System.Activities.NativeActivity.Execute%2A>, передавая ему контекст <xref:System.Activities.NativeActivityContext>. <xref:System.Activities.NativeActivityContext> выполняет для действия роль посредника к среде выполнения для разыменования аргументов и переменных, а также планирования работы других объектов <xref:System.Activities.Activity> или `ActivityDelegates`. `MySequence` использует `InternalExecute` метод для инкапсуляции логики планирования работы первого и всех последующих дочерних элементов в единственном методе. Он начинает свое функционирование с разыменования `currentIndex`. Если это значение равно количеству в коллекции `Activities`, то последовательность завершается, действие выполняет возврат без планирования какой-либо работы и среда выполнения переводит его в состояние <xref:System.Activities.ActivityInstanceState.Closed>. Если `currentIndex` меньше, чем число действий, следующего дочернего элемента извлекается из `Activities` коллекции и `MySequence` вызовы <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, передавая подлежащего планированию дочернего элемента и <xref:System.Activities.CompletionCallback> , указывающий на `InternalExecute` метод. Наконец, значение `currentIndex` увеличивается и управление снова передается среде выполнения. Пока экземпляр действия `MySequence` имеет запланированный дочерний объект <xref:System.Activities.Activity>, среда выполнения считает, что оно находится в состоянии выполнения.

 После завершения дочернего действия выполняется <xref:System.Activities.CompletionCallback>. Выполнение цикла продолжается с его верхней части. Как и метод `Execute`, обратный вызов <xref:System.Activities.CompletionCallback> принимает контекст <xref:System.Activities.NativeActivityContext>, предоставляя средству реализации доступ к среде выполнения.

 `MyWhile` отличается от `MySequence` тем, что он планирует один <xref:System.Activities.Activity> объекта несколько раз, и в нем используется <xref:System.Activities.Activity%601>< bool\> с именем `Condition` для определения, является ли должно быть выполнено это планирование. Как и действие `MySequence`, действие `MyWhile` использует метод `InternalExecute` для централизации своей логики планирования. Оно планирует `Condition`<xref:System.Activities.Activity>< bool\> с <xref:System.Activities.CompletionCallback%601> \<bool > с именем `OnEvaluationCompleted`. После завершения выполнения проверки `Condition` ее результат становится доступным через этот обратный вызов <xref:System.Activities.CompletionCallback> в строго типизированном параметре с именем `result`. Если `true`, `MyWhile` вызовы <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, передавая `Body`<xref:System.Activities.Activity> объекта и `InternalExecute` как <xref:System.Activities.CompletionCallback>. После завершения выполнения `Body` проверка `Condition` планируется еще раз в действии `InternalExecute`, что приводит к очередному запуску цикла. Если проверка `Condition` возвращает значение `false`, экземпляр действия `MyWhile` передает управление среде выполнения без планирования `Body`, а среда выполнения переводит действие в состояние <xref:System.Activities.ActivityInstanceState.Closed>.

#### <a name="to-set-up-build-and-run-the-sample"></a>Настройка, сборка и выполнение образца

1. Откройте образец решения Composite.sln в Visual Studio 2010.

2. Постройте и запустите это решение.

> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры. Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`