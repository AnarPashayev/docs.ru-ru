---
title: -linkresource (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 5555f83107a40b40c7f05c7cc5729f721727f67c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793943"
---
# <a name="-linkresource-visual-basic"></a>-linkresource (Visual Basic)
Создает ссылку на управляемый ресурс.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Аргументы  
 `filename`  
 Обязательный. Файл ресурсов, ссылки на сборку. Если имя файла содержит пробел, заключите имя в кавычки (» «).  
  
 `identifier`  
 Необязательный параметр. Логическое имя ресурса. Имя, которое используется для загрузки ресурса. По умолчанию используется имя файла. При необходимости можно указать, является ли файл открытым или закрытым в манифесте сборки, например: `-linkres:filename.res,myname.res,public`. По умолчанию `filename` является открытым в сборке.  
  
## <a name="remarks"></a>Примечания  
 `-linkresource` Параметр не внедрить файл ресурсов в выходной файл; используйте `-resource` параметр, чтобы это сделать.  
  
 `-linkresource` Параметр требует одного из `-target` параметры, отличные от `-target:module`.  
  
 Если `filename` — [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] файл ресурсов, созданным, например, по [Resgen.exe (генератор файлов ресурсов)](../../../framework/tools/resgen-exe-resource-file-generator.md) или в среде разработки, он может осуществляться с помощью членов пространства <xref:System.Resources> пространства имен. (Дополнительные сведения см. в разделе <xref:System.Resources.ResourceManager>.) Чтобы получить доступ к всем остальным ресурсам во время выполнения, используйте методы, которые начинаются с `GetManifestResource` в <xref:System.Reflection.Assembly> класса.  
  
 Имя файла может иметь любой формат файла. Например, может потребоваться сделать имеющуюся на компьютере библиотеку DLL частью сборки, поэтому ее можно разместить в глобальном кэше сборок и обеспечить к ней доступ из управляемого кода сборки.  
  
 Краткой формой `-linkresource` является `-linkres`.  
  
> [!NOTE]
>  `-linkresource` Параметр недоступен в среде разработки Visual Studio; она доступна только при компиляции из командной строки.  
  
## <a name="example"></a>Пример  
 Следующий код компилирует `in.vb` и ссылки на файл ресурсов `rf.resource`.  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>См. также

- [Компилятор Visual Basic с интерфейсом командной строки](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-ресурсов (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)
- [Примеры командных строк компиляции](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
