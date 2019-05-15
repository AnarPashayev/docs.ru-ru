---
title: Отражение (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 4593aeef13f5d1d0c223b40e266556cb2bcfee5f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595554"
---
# <a name="reflection-c"></a>Отражение (C#)
Механизм отражения позволяет получать объекты (типа <xref:System.Type>), которые описывают сборки, модули и типы. Отражение можно использовать для динамического создания экземпляра типа, привязки типа к существующему объекту, а также получения типа из существующего объекта и вызова его методов или доступа к его полям и свойствам. Если в коде используются атрибуты, отражение обеспечивает доступ к ним. Дополнительные сведения см. в разделе [Атрибуты](../../../../docs/standard/attributes/index.md).  
  
 Вот простой пример отражения, в котором для получения типа переменной используется статический метод `GetType`, наследуемый всеми типами от базового класса `Object`.  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 Результат.  
  
 `System.Int32`  
  
 В этом примере отражение используется для получения полного имени загруженной сборки.  
  
```csharp  
// Using Reflection to get information of an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 Результат.  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  Ключевые слова C# `protected` и `internal` не имеют никакого значения в промежуточном языке и не используются в интерфейсах API отражения. Соответствующими терминами в промежуточном языке являются *Family* и *Assembly*. Для идентификации метода `internal` с помощью отражения используйте свойство <xref:System.Reflection.MethodBase.IsAssembly%2A>. Для идентификации метода `protected internal` используйте <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.  
  
## <a name="reflection-overview"></a>Общие сведения об отражении  
 Отражение удобно использовать в следующих ситуациях:  
  
- При необходимости доступа к атрибутам в метаданных программы. Дополнительные сведения см. в разделе [Извлечение информации, сохраненной в атрибуте](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
- Для проверки и создания экземпляров типов в сборке.  
  
- Для создания типов во время выполнения. Используйте классы в <xref:System.Reflection.Emit>.  
  
- Для выполнения позднего связывания, которое обеспечивает доступ к методам в типах, созданных во время выполнения. См. раздел [Динамическая загрузка и использование типов](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
## <a name="related-sections"></a>Связанные разделы  
 Дополнительные сведения:  
  
- [Отражение](../../../framework/reflection-and-codedom/reflection.md)  
  
- [Просмотр сведений о типах](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [Отражение и универсальные типы](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [Извлечение информации, сохраненной в атрибуте](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)
- [Сборки в среде CLR](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
