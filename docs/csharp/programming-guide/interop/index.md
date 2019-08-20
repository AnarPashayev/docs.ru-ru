---
title: Руководство по программированию на C#. Взаимодействие
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 896f89304289fd90c10da9aaa7ea15ada35ef8f7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589096"
---
# <a name="interoperability-c-programming-guide"></a>Взаимодействие (Руководство по программированию в C#)
Возможность взаимодействия позволяет использовать уже созданный неуправляемый код, экономя средства на разработку. Код, который выполняется под управлением среды CLR, называется *управляемым кодом*, а код, который выполняется вне среды CLR, называется *неуправляемым кодом*. COM, COM +, компоненты C++, компоненты ActiveX и Microsoft Windows API являются примерами неуправляемого кода.  
  
 .NET Framework обеспечивает взаимодействие с неуправляемым кодом посредством служб вызова неуправляемого кода (PInvoke), пространства имен <xref:System.Runtime.InteropServices>, COM-взаимодействия и взаимодействия с C++.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Общие сведения о взаимодействии](./interoperability-overview.md)  
 Описывает способы взаимодействия между управляемым кодом C# и неуправляемым кодом.  
  
 [Практическое руководство. Доступ к объектам взаимодействия Office с помощью функций языка Visual C#](./how-to-access-office-onterop-objects.md)  
 Описывает возможности, представленные в Visual C#, которые упрощают программирование для Office.  
  
 [Практическое руководство. Использование индексированных свойств в программировании COM-взаимодействия](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Описывает использование индексированных свойств для доступа к свойствам COM, которые имеют параметры.  
  
 [Практическое руководство. Использование вызова неуправляемого кода для воспроизведения звукового файла](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Описывает, как использовать платформу вызова служб, чтобы воспроизвести звуковой WAV-файл в операционной системе Windows.  
  
 [Пошаговое руководство. Программирование для Office](./walkthrough-office-programming.md)  
 Описывает процесс создания книги Excel и документа Word со ссылкой на эту книгу.  
  
 [Пример COM-класса](./example-com-class.md)  
 Предлагает пример предоставления класса C# в качестве COM-объекта.  
  
## <a name="c-language-specification"></a>Спецификация языка C#  

Дополнительные сведения см. в разделе [Основные понятия](~/_csharplang/spec/unsafe-code.md) в [Спецификации языка C#](../../language-reference/language-specification/index.md). Спецификация языка является предписывающим источником информации о синтаксисе и использовании языка C#.
  
## <a name="see-also"></a>См. также

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [Руководство по программированию на C#](../index.md)
- [Взаимодействие с неуправляемым кодом](../../../framework/interop/index.md)
- [Пошаговое руководство. Программирование для Office](./walkthrough-office-programming.md)
