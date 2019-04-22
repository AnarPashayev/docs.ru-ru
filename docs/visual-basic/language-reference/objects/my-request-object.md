---
title: Объект My.Request (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 08212dc5fe563ce84be02ab706b56195a0636894
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836627"
---
# <a name="myrequest-object"></a><span data-ttu-id="8d327-102">Объект My.Request</span><span class="sxs-lookup"><span data-stu-id="8d327-102">My.Request Object</span></span>
<span data-ttu-id="8d327-103">Возвращает объект <xref:System.Web.HttpRequest> для запрашиваемой страницы.</span><span class="sxs-lookup"><span data-stu-id="8d327-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d327-104">Примечания</span><span class="sxs-lookup"><span data-stu-id="8d327-104">Remarks</span></span>  
 <span data-ttu-id="8d327-105">Объект `My.Request` содержит сведения о текущем HTTP-запросе.</span><span class="sxs-lookup"><span data-stu-id="8d327-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="8d327-106">Объект `My.Request` доступен только для приложений ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8d327-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d327-107">Пример</span><span class="sxs-lookup"><span data-stu-id="8d327-107">Example</span></span>  
 <span data-ttu-id="8d327-108">Следующий пример получает коллекцию заголовков из `My.Request` и использует `My.Response` объект для записи его на страницу ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8d327-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8d327-109">См. также</span><span class="sxs-lookup"><span data-stu-id="8d327-109">See also</span></span>

- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="8d327-110">Объект My.Response</span><span class="sxs-lookup"><span data-stu-id="8d327-110">My.Response Object</span></span>](../../../visual-basic/language-reference/objects/my-response-object.md)
