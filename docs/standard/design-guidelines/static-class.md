---
title: Разработка статичных классов
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
author: KrzysztofCwalina
ms.openlocfilehash: d0a2f11b53f50f2ec2f301f7b88df65e1cd7b811
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762050"
---
# <a name="static-class-design"></a>Разработка статичных классов
Статический класс представляет собой класс, который содержит только статические члены (Конечно, помимо экземпляр членам, унаследованным от <xref:System.Object?displayProperty=nameWithType> и возможно закрытый конструктор). Некоторые языки предоставляют встроенную поддержку для статических классов. В C# 2.0 и более поздних версий когда класс объявлен как статический, это запечатанный, абстрактный, и нет членов экземпляров можно переопределить или объявлен.  
  
 Статические классы — это компромисс между чисто объектно ориентированного проектирования и простотой. Они часто используются для предоставления ярлыки для других операций (таких как <xref:System.IO.File?displayProperty=nameWithType>), владельцы методы расширения, или функции, для которой полное объектно ориентированную оболочку несанкционированному (такие как <xref:System.Environment?displayProperty=nameWithType>).  
  
 **✓ DO** статические классы предназначены для использования только в случае необходимости.  
  
 Статические классы должны использоваться только в качестве вспомогательных классов для объектно-ориентированной платформы.  
  
 **X DO NOT** используйте статические классы как всевозможных объектов.  
  
 **X DO NOT** объявления или переопределять члены экземпляра в статических классах.  
  
 **✓ DO** объявить как запечатанный, абстрактный статических классов и добавьте конструктор закрытого экземпляра, если язык программирования не предусмотрена встроенная поддержка статических классов.  
  
 *Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*  
  
 *Перепечатано разрешением Пирсона для образовательных учреждений, Inc. из [рекомендации по разработке Framework: Условные обозначения, стили и шаблоны для библиотеки .NET для повторного использования, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Кшиштов Квалина и Брэд Абрамс, опубликованных 22 октября 2008 г., издательство Addison-Wesley Professional как части цикла разработки Microsoft Windows.*  
  
## <a name="see-also"></a>См. также

- [Рекомендации по разработке типов](../../../docs/standard/design-guidelines/type.md)
- [Рекомендации по проектированию на основе Framework](../../../docs/standard/design-guidelines/index.md)
