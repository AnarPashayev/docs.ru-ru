---
title: Руководство по программированию на C#. Использование конструкторов
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 14ff272fe940c265dc8984d6b20985bb2d2ba12d
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398251"
---
# <a name="using-constructors-c-programming-guide"></a>Использование конструкторов (Руководство по программированию на C#)

Каждый раз, когда создается [класс](../../../csharp/language-reference/keywords/class.md) или [структура](../../../csharp/language-reference/keywords/struct.md), вызывается конструктор. Конструкторы имеют имя, совпадающее с именем класса или структуры, и обычно инициализируют члены данных нового объекта.  
  
 В следующем примере класс с именем `Taxi` определяется с помощью простого конструктора. Затем оператор [new](../../../csharp/language-reference/operators/new-operator.md) создает экземпляр этого класса. Конструктор `Taxi` вызывается оператором `new` сразу после того, как новому объекту будет выделена память.  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 Конструктор, который не принимает никаких параметров, называется *конструктором без параметров*. Конструкторы по умолчанию вызываются всякий раз, когда создается экземпляр объекта с помощью оператора `new`, а аргументы в `new` не передаются. Дополнительные сведения см. в разделе [Конструкторы экземпляров](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Если класс не является [статическим](../../../csharp/language-reference/keywords/static.md), компилятор C# выделяет классам без конструкторов открытый конструктор без параметров, позволяющий создавать экземпляры классов. Дополнительные сведения см. в статье [Статические классы и члены статических классов](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Создание экземпляров класса можно запретить, сделав конструктор закрытым, следующим образом:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Дополнительные сведения см. в разделе [Закрытые конструкторы](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).  
  
 Конструкторы для типов [struct](../../../csharp/language-reference/keywords/struct.md) похожи на конструкторы классов, однако `structs` не может содержать явный конструктор без параметров, так как он предоставляется компилятором автоматически. Этот конструктор инициализирует каждое поле в `struct` со значением по умолчанию. Дополнительные сведения см. в разделе [Таблица значений по умолчанию](../../../csharp/language-reference/keywords/default-values-table.md). При этом конструктор без параметров вызывается только в том случае, если экземпляр `struct` создается с помощью переменной `new`. Например, в этом коде конструктор без параметров используется для <xref:System.Int32> — это обеспечивает инициализацию целого числа:  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 В то же время следующий код вызывает ошибку компилятора, поскольку не использует `new`, и потому, что использует не инициализированный объект:  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 Кроме того, объекты на основе `structs` (включая все встроенные числовые типы) можно инициализировать или назначить, а затем использовать, как в следующем примере:  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 В связи с этим вызывать конструктор без параметров для типа значения необязательно.  
  
 Оба класса и `structs` могут определять конструкторы, принимающие параметры. Конструкторы, принимающие параметры, необходимо вызывать с помощью оператора `new` или [base](../../../csharp/language-reference/keywords/base.md). Классы и `structs` могут определять также несколько конструкторов; для определения конструктора без параметров ни один их них не требуется. Например:  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 Этот класс можно создать, воспользовавшись одним из следующих операторов:  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 Конструктор может использовать ключевое слово `base` для вызова конструктора базового класса. Например:  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 В этом примере конструктор базового класса вызывается перед выполнением соответствующего ему блока. Ключевое слово `base` можно использовать как с параметрами, так и без них. Любые параметры для конструктора можно использовать как параметры для `base` или как часть выражения. Дополнительные сведения см. в разделе [base](../../../csharp/language-reference/keywords/base.md).  
  
 В производном классе, если конструктор базового класса не вызывается явным образом с помощью ключевого слова `base`, конструктор без параметров, если он существует, вызывается неявно. Это означает, что следующие объявления конструкторов действуют одинаково:  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 Если базовый класс не предлагает конструктор без параметров, производный класс должен явно вызвать конструктор базового класса с помощью `base`.  
  
 Конструктор может вызывать другой конструктор в том же объекте с помощью ключевого слова [this](../../../csharp/language-reference/keywords/this.md). Как и `base`, `this` можно использовать с параметрами или без, а все параметры в конструкторе доступны как параметры `this` или как часть выражения. Например, второй конструктор в предыдущем примере можно переписать, используя `this`:  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 Применение ключевого слова `this` в приведенном выше примере привело к вызову конструктора:  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 Конструкторы могут иметь пометку [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) или [private protected](../../../csharp/language-reference/keywords/private-protected.md). Эти модификаторы доступа определяют, каким образом пользователи класса смогут создавать класс. Дополнительные сведения см. в статье [Модификаторы доступа](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Конструктор можно объявить статическим, используя ключевое слово [static](../../../csharp/language-reference/keywords/static.md). Статические конструкторы вызываются автоматически непосредственно перед доступом к статическим полям и обычно используются для инициализации членов статического класса. Дополнительные сведения см. в разделе [Статические конструкторы](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="c-language-specification"></a>Спецификация языка C#  

Дополнительные сведения см. в разделах [Конструкторы экземпляров](~/_csharplang/spec/classes.md#instance-constructors) и [Статические конструкторы](~/_csharplang/spec/classes.md#static-constructors) в [Спецификации языка C#](../../language-reference/language-specification/index.md). Спецификация языка является предписывающим источником информации о синтаксисе и использовании языка C#.
  
## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)
- [Классы и структуры](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Конструкторы](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Методы завершения](../../../csharp/programming-guide/classes-and-structs/destructors.md)
