---
title: Практическое руководство. Как обеспечить сериализации сущностей
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: bbe40ec448bef5f62d4182d96f82c6308639e27f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033804"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="27e2f-102">Практическое руководство. Как обеспечить сериализации сущностей</span><span class="sxs-lookup"><span data-stu-id="27e2f-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="27e2f-103">Возможность сериализации сущностей можно обеспечить при создании кода.</span><span class="sxs-lookup"><span data-stu-id="27e2f-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="27e2f-104">К классам сущностей добавляется атрибут <xref:System.Runtime.Serialization.DataContractAttribute>, а к столбцам - атрибут <xref:System.Runtime.Serialization.DataMemberAttribute>.</span><span class="sxs-lookup"><span data-stu-id="27e2f-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="27e2f-105">С помощью Visual Studio разработчики могут использовать [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] для этой цели.</span><span class="sxs-lookup"><span data-stu-id="27e2f-105">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for this purpose.</span></span>  
  
 <span data-ttu-id="27e2f-106">Если вы используете средство командной строки SQLMetal, использовать **/serialization** с параметром `unidirectional` аргумент.</span><span class="sxs-lookup"><span data-stu-id="27e2f-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="27e2f-107">Дополнительные сведения см. в разделе [SQLMetal.exe (средство создания кода)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="27e2f-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="27e2f-108">Пример</span><span class="sxs-lookup"><span data-stu-id="27e2f-108">Example</span></span>  
 <span data-ttu-id="27e2f-109">В следующих командах средства командной строки SQLMetal создают файлы, содержащие сериализуемые сущности.</span><span class="sxs-lookup"><span data-stu-id="27e2f-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="27e2f-110">См. также</span><span class="sxs-lookup"><span data-stu-id="27e2f-110">See also</span></span>

- [<span data-ttu-id="27e2f-111">Сериализация</span><span class="sxs-lookup"><span data-stu-id="27e2f-111">Serialization</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)
- [<span data-ttu-id="27e2f-112">Создание модели объектов</span><span class="sxs-lookup"><span data-stu-id="27e2f-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
