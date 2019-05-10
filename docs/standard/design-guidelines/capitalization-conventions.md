---
title: Соглашения о написании прописными буквами
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
author: KrzysztofCwalina
ms.openlocfilehash: e0da4cd747846921d170d9c07d6f1fb91dbd4ed7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615257"
---
# <a name="capitalization-conventions"></a>Соглашения о написании прописными буквами
Рекомендации в этой главе размещать простой метод с помощью варианта, когда применяется последовательно, делать идентификаторы для типов, членов и параметров, удобном для чтения.  
  
## <a name="capitalization-rules-for-identifiers"></a>Регистр букв правилам для идентификаторов  
 Для разделения слов в идентификаторе, преобразование первой буквы каждого слова в идентификаторе. Не используйте символы подчеркивания для разделения слов, или для того, где угодно в идентификаторах. Существует два способа соответствующие прописной идентификаторов, в зависимости от использования идентификатора:  
  
- PascalCasing  
  
- camelCasing  
  
 Соглашение PascalCasing, применяется для всех идентификаторов, за исключением имен параметров, первая буква каждого слова (включая акронимов через двух букв), как показано в следующих примерах:  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 Особый случай выполняется для двухбуквенный акронимов, в которых заданы оба буквы, как показано в следующий идентификатор:  
  
 `IOStream`  
  
 Соглашение camelCasing, применяется только для имен параметров, первая буква каждого слова, кроме первого, как показано в следующих примерах. В примере также показано, как строчные, двухбуквенный сокращений, которые начинаются с идентификатора Camel.  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **✓ DO** использовать PascalCasing для всех открытых элемента, типа и пространство имен имен, состоящих из нескольких слов.  
  
 **✓ DO** использовать camelCasing для имен параметров.  
  
 Следующая таблица описывает правила использования прописных букв для различных типов идентификаторов.  
  
|Идентификатор|Регистр|Пример|  
|----------------|------------|-------------|  
|Пространство имен|Pascal|`namespace System.Security { ... }`|  
|Тип|Pascal|`public class StreamReader { ... }`|  
|Интерфейс|Pascal|`public interface IEnumerable { ... }`|  
|Метод|Pascal|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|Свойство|Pascal|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|событие|Pascal|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|Поле|Pascal|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|Значение перечисления|Pascal|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|Параметр|Camel|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>Составные слова в прописную букву и распространенные термины  
 Большинство составные термины рассматриваются как отдельные слова в рамках регистр букв.  
  
 **X DO NOT** прописных так называемые единым составные слова.  
  
 Это сложные слова, записываются в одно слово, например конечной точки. Целью правила учета регистра обрабатывать составное слово единым как одно слово. Используйте текущий словарь для определения того, если составное слово записывается в закрытой формой.  
  
|Pascal|Camel|not|  
|------------|-----------|---------|  
|`BitFlag`|`bitFlag`|`Bitflag`|  
|`Callback`|`callback`|`CallBack`|  
|`Canceled`|`canceled`|`Cancelled`|  
|`DoNot`|`doNot`|`Don't`|  
|`Email`|`email`|`EMail`|  
|`Endpoint`|`endpoint`|`EndPoint`|  
|`FileName`|`fileName`|`Filename`|  
|`Gridline`|`gridline`|`GridLine`|  
|`Hashtable`|`hashtable`|`HashTable`|  
|`Id`|`id`|`ID`|  
|`Indexes`|`indexes`|`Indices`|  
|`LogOff`|`logOff`|`LogOut`|  
|`LogOn`|`logOn`|`LogIn`|  
|`Metadata`|`metadata`|`MetaData, metaData`|  
|`Multipanel`|`multipanel`|`MultiPanel`|  
|`Multiview`|`multiview`|`MultiView`|  
|`Namespace`|`namespace`|`NameSpace`|  
|`Ok`|`ok`|`OK`|  
|`Pi`|`pi`|`PI`|  
|`Placeholder`|`placeholder`|`PlaceHolder`|  
|`SignIn`|`signIn`|`SignOn`|  
|`SignOut`|`signOut`|`SignOff`|  
|`UserName`|`userName`|`Username`|  
|`WhiteSpace`|`whiteSpace`|`Whitespace`|  
|`Writable`|`writable`|`Writeable`|  
  
## <a name="case-sensitivity"></a>Учет регистра  
 Языки, которые могут выполняться в среде CLR не требуются для поддержки учета регистра, несмотря на то, что некоторые делают. Даже если ваш язык поддерживает такую возможность, другими языками, может получить доступ к вашей платформы — нет. Любой API, которые будут доступны извне, таким образом, нельзя полагаться на случай отдельно, чтобы различать два имени, в том же контексте.  
  
 **X DO NOT** предполагается, что все языки программирования чувствительны к регистру. Это не так. Имена не могут различаться только регистром.  
  
 *Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*  
  
 *Перепечатано разрешением Пирсона для образовательных учреждений, Inc. из [рекомендации по разработке Framework: Условные обозначения, стили и шаблоны для библиотеки .NET для повторного использования, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Кшиштов Квалина и Брэд Абрамс, опубликованных 22 октября 2008 г., издательство Addison-Wesley Professional как части цикла разработки Microsoft Windows.*  
  
## <a name="see-also"></a>См. также

- [Рекомендации по проектированию на основе Framework](../../../docs/standard/design-guidelines/index.md)
- [Правила именования](../../../docs/standard/design-guidelines/naming-guidelines.md)
