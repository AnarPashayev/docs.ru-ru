---
title: разрешение загрузки сборок
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET Framework], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ed4533c934120c3400ddba68e65bc82aabc9370
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456770"
---
# <a name="resolving-assembly-loads"></a>разрешение загрузки сборок
В .NET Framework имеется событие <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> для приложений, требующих дополнительного управления загрузкой сборок. Обрабатывая это событие, приложение может загружать сборку в контекст загрузки не из каталогов, где обычно осуществляется поиск, выбирать, какую из версий сборки загрузить, создавать динамическую сборку и возвращать ее и многое другое. В этом разделе описывается использование события <xref:System.AppDomain.AssemblyResolve>.  
  
> [!NOTE]
>  Для разрешения загрузки сборок в контексте только для отражения используйте событие <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType>.  
  
## <a name="how-the-assemblyresolve-event-works"></a>Как Принцип действия события AssemblyResolve  
 При регистрации обработчика для события <xref:System.AppDomain.AssemblyResolve> обработчик вызывается каждый раз, когда среда выполнения не может связать сборку по имени. Например, вызов следующих методов из пользовательского кода может привести к возникновению события <xref:System.AppDomain.AssemblyResolve>.  
  
- Перегрузка метода <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> или перегрузка метода <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, где первым аргументом является строка, представляющая отображаемое имя загружаемой сборки (то есть строка, возвращаемая свойством <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>).  
  
- Перегрузка метода <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> или перегрузка метода <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, где первым аргументом является объект <xref:System.Reflection.AssemblyName>, идентифицирующий загружаемую сборку.  
  
- Перегрузка метода <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
- Перегрузка метода <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> или <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>, создающая объект в другом домене приложения.  
  
### <a name="what-the-event-handler-does"></a>Действие обработчика событий  
 Обработчик события <xref:System.AppDomain.AssemblyResolve> получает отображаемое имя сборки, которую необходимо загрузить, в свойстве <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType>. Если обработчик не распознает имя сборки, он возвращает значение NULL (`Nothing` в Visual Basic, `nullptr` в Visual C++).  
  
 Если обработчик распознает имя сборки, он может загрузить и вернуть сборку, отвечающую запросу. Ниже перечислены некоторые возможные сценарии.  
  
- Если обработчик знает место расположения версии сборки, он может загрузить сборку с помощью метода <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> или <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> и, если все прошло удачно, вернуть загруженную сборку.  
  
- Если у обработчика есть доступ к базе данных сборок, хранимых в виде массивов байтов, он может загрузить массив байтов с помощью одной из перегрузок метода <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, принимающих массив байтов.  
  
- Обработчик может создать динамическую сборку и вернуть ее.  
  
> [!NOTE]
>  Обработчик должен загружать сборку в контекст, из которого ведется загрузка, в контекст загрузки или без контекста. Если обработчик загружает сборку в контекст только для отражения с помощью метода <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> или <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType>, попытка загрузки, вызвавшая событие <xref:System.AppDomain.AssemblyResolve>, завершается неудачно.  
  
 Ответственность за возврат подходящей сборки лежит на обработчике событий. Обработчик может обработать отображаемое имя запрошенной сборки, передав значение свойства <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> в конструктор <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29>. Начиная с [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], обработчик может использовать свойство <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> для определения, находится ли текущий запрос в зависимости от другой сборки. Эта информация может помочь найти сборку, которая удовлетворит зависимость.  
  
 Обработчик событий может вернуть версию сборки, отличную от запрошенной.  
  
 В большинстве случаев сборка, возвращенная обработчиком, появляется в контексте загрузки, независимо от контекста, в который загружает ее обработчик. Например, если обработчик использует метод <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> для загрузки сборки в контекст, из которого ведется загрузка, сборка появляется в контексте загрузки, когда обработчик возвращает ее. Но в следующем случае возвращенная обработчиком сборка появится без контекста.  
  
- Обработчик загружает сборку без контекста.  
  
- Значение свойства <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> отличается от NULL.  
  
- Запрашивающая сборка (то есть сборка, возвращенная свойством <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType>) загружена без контекста.  
  
 Сведения о контекстах см. в разделе о перегрузке метода <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType>.  
  
 Несколько версий одной сборки можно загрузить в один домен приложения. Делать так не рекомендуется, так как это может привести к проблемам назначения типа. См. раздел [Рекомендации для загрузки сборок](../../../docs/framework/deployment/best-practices-for-assembly-loading.md).  
  
### <a name="what-the-event-handler-should-not-do"></a>Чего не должен делать обработчик событий  
 Основное правило обработки события <xref:System.AppDomain.AssemblyResolve> заключается в том, что не следует пытаться вернуть сборку, которая не распознается. При написании обработчика следует учитывать, какие сборки могут вызвать событие. Обработчик должен возвращать значение NULL для других сборок.  
  
> [!IMPORTANT]
>  Начиная с .NET Framework 4 событие <xref:System.AppDomain.AssemblyResolve> вызывается для вспомогательных сборок. Это изменение затрагивает обработчик событий, написанный для более ранней версии .NET Framework, если обработчик пытается разрешить все запросы на загрузку сборок. Это изменение не затрагивает обработчики событий, игнорирующие нераспознанные сборки. Такие обработчики возвращают значение NULL, и срабатывают обычные резервные механизмы.  
  
 При загрузке сборки обработчик событий не должен использовать какую-либо из перегрузок метода <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> или <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, которые могут вызвать рекурсивное возникновение события <xref:System.AppDomain.AssemblyResolve>, так как это может привести к переполнению стека. (См. список выше в этом разделе.) Это происходит, даже если обрабатывать исключения, так как исключение не создается, пока все обработчики событий не закончат возврат. Таким образом, следующий код приведет к переполнению стека, если объект `MyAssembly` не будет найден.  
  
 [!code-cpp[AssemblyResolveRecursive#1](../../../samples/snippets/cpp/VS_Snippets_CLR/assemblyresolverecursive/cpp/example.cpp#1)]
 [!code-csharp[AssemblyResolveRecursive#1](../../../samples/snippets/csharp/VS_Snippets_CLR/assemblyresolverecursive/cs/example.cs#1)]
 [!code-vb[AssemblyResolveRecursive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/assemblyresolverecursive/vb/example.vb#1)]  
  
## <a name="see-also"></a>См. также

- [Рекомендации для загрузки сборок](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)
- [Использование доменов приложений](../../../docs/framework/app-domains/use.md)
