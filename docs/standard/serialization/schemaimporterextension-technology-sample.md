---
title: Образец технологии SchemaImporterExtension
ms.date: 03/30/2017
ms.assetid: 3f5eb78f-0ef6-433a-b095-3a63b1ce0bc9
ms.openlocfilehash: 5027897bcf62e52dae5aab6090c01518a92636dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62028308"
---
# <a name="schemaimporterextension-technology-sample"></a>Образец технологии SchemaImporterExtension
[Скачать образец](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/SchemaImporterExtension.zip.exe)  
  
 В этом образце демонстрируется пользовательский класс <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension>, позволяющий более точно управлять формированием кода при импорте схемы XML. C помощью этого приложения показывается, как выполнять построение, регистрировать и вызывать это расширение.  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>Сборка образца с использованием командной строки  
  
1. Откройте окно командной строки и перейдите к вложенной папке для данного образца, соответствующей выбранному языку.  
  
2. В командной строке введите **msbuild.exe OrderSchemaImporterExtension.sln**.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Сборка образца с использованием Visual Studio  
  
1. Откройте [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] и перейдите к вложенной папке для данного образца, соответствующей выбранному языку.  
  
2. Дважды щелкните значок OrderSchemaImporterExtension.sln, чтобы открыть файл в Visual Studio.  
  
3. В меню **Сборка** выберите **Собрать решение**.  
  
 По умолчанию построение приложения помещается в каталог \bin или \bin\Debug.  
  
### <a name="to-run-the-sample"></a>Выполнение образца  
  
1. С помощью командной строки перейдите в каталог, содержащий новый исполняемый файл.  
  
2. В командной строке введите **[exe имя]**.  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о создании примера двоичного файла и шагах по его регистрации см. в комментариях в файле исходного кода и файле build.proj.  
  
## <a name="see-also"></a>См. также

- <xref:System.CodeDom.CodeCompileUnit>
- <xref:System.CodeDom.CodeNamespace>
- <xref:System.CodeDom.CodeNamespaceImport>
- <xref:Microsoft.CSharp.CSharpCodeProvider>
- <xref:System.Xml.Serialization.IXmlSerializable>
- <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension>
- <xref:System.CodeDom>
- <xref:System.CodeDom.Compiler>
- <xref:System.Web.Services.Description>
- <xref:System.Web.Services.Discovery>
- <xref:System.Xml.Serialization>
- <xref:System.Uri>
- <xref:Microsoft.VisualBasic.VBCodeProvider>
- <xref:System.Web.Services.Description.WebReference>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
