---
title: bindingFailure MDA
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e904d452b9f4a1b172d35984b752c0d97228338
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480954"
---
# <a name="bindingfailure-mda"></a>bindingFailure MDA

Помощник по отладке управляемого кода (MDA) `bindingFailure` запускается в случае сбоя при загрузке сборки.

## <a name="symptoms"></a>Симптомы

Код попытался загрузить сборку с использованием статической ссылки или одного из методов загрузчика, такого как <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> или <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>. Сборка не загружается, в результате чего возникает исключение <xref:System.IO.FileNotFoundException> или <xref:System.IO.FileLoadException>.

## <a name="cause"></a>Причина

Если среде выполнения не удается загрузить сборку, происходит сбой привязки. Сбой привязки может возникать в одной из следующих ситуаций:

- Общеязыковой среде выполнения (CLR) не удается найти запрошенную сборку. Это может быть вызвано самыми разными причинами, например отсутствием установленной сборки или некорректной конфигурацией поиска сборок в приложении.

- Типичный сценарий возникновения проблемы связан с передачей типа в другой домен приложения, которому требуется среда CLR для загрузки сборки, содержащей этот тип, в другом домене приложения. Если конфигурация другого домена приложения отличается от исходного, при загрузке сборки среда выполнения может столкнуться с ошибкой. Например, в этих двух доменах приложений могут быть установлены разные значения свойства <xref:System.AppDomain.BaseDirectory%2A>.

- Запрошенная сборка повреждена или не является сборкой.

- Код, который пытается загрузить сборку, не имеет разрешений на управление доступом для кода, необходимых для загрузки сборок.

- Учетные данные пользователя не предоставляют разрешений, необходимых для чтения файла.

## <a name="resolution"></a>Решение

В первую очередь необходимо определить причины, по которым среде CLR не удается выполнить привязку к запрошенной сборке. Существует много различных причин, по которым среде выполнения не удается найти или загрузить запрошенную сборку. Некоторые из них перечислены в разделе "Причина". Чтобы устранить причину сбоя привязки, рекомендуется выполнить следующие действия:

- Определите причину, используя данные, предоставленные помощником по отладке управляемого кода `bindingFailure`:

  - Запустите программу [Fuslogvw.exe (средство просмотра журнала привязки сборок)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) для чтения журналов ошибок, создаваемых средством привязки сборок.

  - Определите, находится ли запрошенная сборка в указанном месте. В случае методов <xref:System.Reflection.Assembly.LoadFrom%2A> и <xref:System.Reflection.Assembly.LoadFile%2A> запрошенное расположение можно легко определить. При использовании метода <xref:System.Reflection.Assembly.Load%2A>, который осуществляет привязку по удостоверению сборки, необходимо определить сборки, соответствующие этому удостоверению, в пути пробы свойства <xref:System.AppDomain.BaseDirectory%2A> домена приложений и глобальном кэше сборок.

- Устраните выявленные ранее причины. Возможны следующие варианты решения проблемы:

  - Установите запрошенную сборку в глобальный кэш сборок и вызовите <xref:System.Reflection.Assembly.Load%2A> метод для загрузки сборки по удостоверению.

  - Скопируйте запрошенную сборку в каталог приложения и вызовите метод <xref:System.Reflection.Assembly.Load%2A> для загрузки сборки по удостоверению.

  - Измените конфигурацию домена приложения, в котором произошел сбой привязки, включив в нее путь к сборке. Для этого измените значение свойства <xref:System.AppDomain.BaseDirectory%2A> или добавьте частные пути пробы.

  - Измените список управления доступом и разрешите чтение файла для выполнивших вход пользователей.

## <a name="effect-on-the-runtime"></a>Влияние на среду выполнения

Этот помощник отладки управляемого кода не оказывает никакого влияния на среду CLR. Он только создает отчеты о сбоях привязки.

## <a name="output"></a>Вывод

Этот помощник по отладке управляемого кода создает отчет о сбое при загрузке сборок, в который включаются запрошенный путь и (или) отображаемое имя, контекст привязки, домен приложения, в котором была запрошена загрузка, а также причина сбоя.

Если среде CLR недоступны соответствующие данные, отображаемое имя и запрошенный путь могут быть пустыми. Если сбоем завершается вызов метода <xref:System.Reflection.Assembly.Load%2A>, чаще всего среде выполнения не удается определить отображаемое имя сборки.

## <a name="configuration"></a>Параметр Configuration

```xml
<mdaConfig>
  <assistants>
    <bindingFailure />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Пример

В следующем примере кода показана ситуация, которая может привести к запуску помощника по отладке управляемого кода:

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.Reflection;
namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            // This call attempts to load a nonexistent assembly.
            // The call will throw a System.IO.FileNotFound exception
            // and cause the activation of the bindingFailure MDA
            // if it is registered.
            Assembly.Load("NonExistentAssembly");
        }
    }
}
```

## <a name="see-also"></a>См. также

- [Диагностика ошибок посредством управляемых помощников по отладке](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
