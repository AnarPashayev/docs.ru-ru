---
title: Имя <namespacename> в корневом пространстве имен <fullnamespacename> не является CLS-совместимым
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: b03a50365122c17fa311a284bd6995d1af2631c3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401541"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a>Имя \<namespacename> в корневом пространстве имен \<fullnamespacename> не является CLS-совместимым
Сборка помечена как `<CLSCompliant(True)>` , но элемент имени корневого пространства имен начинается с символа подчеркивания ( `_` ).  
  
 Программный элемент может содержать один или несколько символов подчеркивания, но для соответствия [языковым независимостьм и зависимым от языка компонентам](../../../standard/language-independence-and-language-independent-components.md) (CLS) он не должен начинаться с символа подчеркивания. См. раздел [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 При применении атрибута <xref:System.CLSCompliantAttribute> к программному элементу вы задаете для параметра `isCompliant` атрибута значение `True` или `False` , чтобы указать совместимость или несовместимость. Для этого параметра нет значения по умолчанию, и вы должны предоставить значение.  
  
 Если вы не применяете <xref:System.CLSCompliantAttribute> к элементу, он считается несовместимым.  
  
 По умолчанию данное сообщение является предупреждением. Сведения о сокрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Идентификатор ошибки:** BC40039  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Если требуется совместимость с CLS, измените имя корневого пространства имен так, чтобы ни один из его элементов не начинался с символа подчеркивания.  
  
- Если требуется, чтобы имя пространства имен оставалось без изменений, удалите <xref:System.CLSCompliantAttribute> из сборки или пометьте его как `<CLSCompliant(False)>` .  
  
## <a name="see-also"></a>См. также раздел

- [Оператор Namespace](../statements/namespace-statement.md)
- [Пространства имен в Visual Basic](../../programming-guide/program-structure/namespaces.md)
- [-rootnamespace](../../reference/command-line-compiler/rootnamespace.md)
- [Страница "Приложение" в конструкторе проектов (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [Соглашения об именах Visual Basic](../../programming-guide/program-structure/naming-conventions.md)
