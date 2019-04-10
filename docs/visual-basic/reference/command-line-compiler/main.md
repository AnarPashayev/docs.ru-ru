---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: fd6240faf702ccb5e543bfd6a7779284f38d8850
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337244"
---
# <a name="-main"></a>-main
Задает класс или модуль, содержащий процедуру `Sub Main`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-main:location  
```  
  
## <a name="arguments"></a>Аргументы  
 `location`  
 Обязательный. Имя класса или модуля, содержащего `Sub Main` процедуры, который должен вызываться при запуске программы. Это может быть в форме **-main: модуль** или **-main:namespace.module**.  
  
## <a name="remarks"></a>Примечания  
 Используйте этот параметр при создании исполняемого файла или исполняемой программы Windows. Если **-основной** параметр указан, компилятор выполняет поиск допустимый общий `Sub Main` во всех открытых классов и модулей.  
  
 См. в разделе [процедура Main в Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) обсуждение различных видов `Main` процедуры.  
  
 Когда `location` — это класс, который наследует от <xref:System.Windows.Forms.Form>, компилятор предоставляет значение по умолчанию `Main` процедуру, которая запускает приложение, если класс не имеет `Main` процедуры. Это позволяет скомпилировать код из командной строки, который был создан в среде разработки.  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>Чтобы задать - основной в среде разработки Visual Studio  
  
1. Выберите проект в **Обозревателе решений**. В меню **Проект** выберите пункт **Свойства**.  
  
2. Перейдите на вкладку **Приложение** .  
  
3. Убедитесь, что **Включить исполняющую** не установлен флажок.  
  
4. Измените значение в **автоматически запускаемый объект** поле.  
  
## <a name="example"></a>Пример  
 Следующий код компилирует `T2.vb` и `T3.vb`, указав, `Sub Main` процедуры будут находиться в `Test2` класса.  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>См. также

- [Компилятор Visual Basic с интерфейсом командной строки](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Примеры командных строк компиляции](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Процедура Main в Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
