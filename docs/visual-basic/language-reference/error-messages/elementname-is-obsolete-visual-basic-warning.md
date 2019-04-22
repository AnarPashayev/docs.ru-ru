---
title: <elementname> является устаревшим (Предупреждение Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: 545f0f4a56e72e32d2225217225d441a10f0e52e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836367"
---
# <a name="elementname-is-obsolete-visual-basic-warning"></a><span data-ttu-id="7ddae-102">"\<elementname >" является устаревшим (предупреждение Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ddae-102">'\<elementname>' is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="7ddae-103">Оператор пытается получить доступ к элементу программирования, который был помечен атрибутом <xref:System.ObsoleteAttribute> и директивой, предписывающей расценивать это как предупреждение.</span><span class="sxs-lookup"><span data-stu-id="7ddae-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="7ddae-104">Вы можете пометить любой программный элемент как неиспользуемый, применив к нему <xref:System.ObsoleteAttribute> .</span><span class="sxs-lookup"><span data-stu-id="7ddae-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="7ddae-105">Если вы это сделаете, вы можете задать для свойства <xref:System.ObsoleteAttribute.IsError%2A> атрибута значение `True` или `False`.</span><span class="sxs-lookup"><span data-stu-id="7ddae-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="7ddae-106">Если задать значение `True`, компилятор будет рассматривать попытку использовать элемент как ошибку.</span><span class="sxs-lookup"><span data-stu-id="7ddae-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="7ddae-107">Если задать значение `False`или оставить значение по умолчанию `False`, то при попытке использовать элемент компилятор выдаст предупреждение.</span><span class="sxs-lookup"><span data-stu-id="7ddae-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="7ddae-108">По умолчанию это сообщение считается предупреждением, так как свойство <xref:System.ObsoleteAttribute.IsError%2A> <xref:System.ObsoleteAttribute> имеет значение `False`.</span><span class="sxs-lookup"><span data-stu-id="7ddae-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="7ddae-109">Дополнительные сведения о сокрытии предупреждений и обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="7ddae-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="7ddae-110">**Идентификатор ошибки:** BC40008</span><span class="sxs-lookup"><span data-stu-id="7ddae-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7ddae-111">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="7ddae-111">To correct this error</span></span>  
  
-   <span data-ttu-id="7ddae-112">Убедитесь, что в ссылке исходного кода имя элемента указано правильно.</span><span class="sxs-lookup"><span data-stu-id="7ddae-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ddae-113">См. также</span><span class="sxs-lookup"><span data-stu-id="7ddae-113">See also</span></span>

- [<span data-ttu-id="7ddae-114">Обзор атрибутов</span><span class="sxs-lookup"><span data-stu-id="7ddae-114">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
