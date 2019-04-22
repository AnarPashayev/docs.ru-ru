---
title: Практическое руководство. Сворачивание и скрытие частей кода (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: bf2a7188456097ac227039e4d902a14eb182664c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822305"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Практическое руководство. Сворачивание и скрытие частей кода (Visual Basic)
`#Region` Директива позволяет сворачивать и скрывать разделы кода в файлах Visual Basic. `#Region` Директива позволяет указать блок кода, который можно разворачивать и сворачивать при использовании в редакторе кода Visual Studio. Возможность выборочно скрыть код делает файлы стала более управляемой и более удобными для чтения. Дополнительные сведения см. в разделе [Структура](/visualstudio/ide/outlining).  
  
 `#Region` директивы поддерживают семантики блока кода, такие как `#If...#End If`. Это означает, что они не может начинаться в одном блоке и заканчиваться в другом; Начало и конец должны быть в одном блоке. `#Region` директивы не поддерживаются в функциях.  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>Чтобы свернуть и скрыть часть кода  
  
-   Поместите раздел кода между `#Region` и `#End Region` инструкции, как показано в следующем примере:  
  
     [!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]  
  
     `#Region` Блок может использоваться несколько раз в файле кода; таким образом, пользователи могут определять свои собственные блоки процедур и классов, которые в свою очередь, может быть свернута. `#Region` блоки также могут быть вложены в другие `#Region` блоков.  
  
    > [!NOTE]
    >  Скрытие кода не препятствует его компиляции и не влияет на `#If...#End If` инструкций.  
  
## <a name="see-also"></a>См. также

- [Условная компиляция](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [Директива #Region](../../../visual-basic/language-reference/directives/region-directive.md)
- [Директивы #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Структура](/visualstudio/ide/outlining)
