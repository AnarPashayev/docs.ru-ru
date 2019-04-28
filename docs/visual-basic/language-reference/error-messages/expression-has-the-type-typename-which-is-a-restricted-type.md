---
title: Выражение имеет тип <typename> который является ограниченным и не может использоваться для доступа к членам, унаследованным от Object или ValueType
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 017a2458562068727674bd3fd9cda8c33d989e8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803172"
---
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a><span data-ttu-id="4cb0e-102">Выражение имеет тип "\<typename >" которого является ограниченным типом и не может использоваться для доступа к членам, унаследованным из «Object» или «ValueType»</span><span class="sxs-lookup"><span data-stu-id="4cb0e-102">Expression has the type '\<typename>' which is a restricted type and cannot be used to access members inherited from 'Object' or 'ValueType'</span></span>
<span data-ttu-id="4cb0e-103">Выражение, результатом которого является тип, который не может быть упакован-преобразован средой общеязыковой среды выполнения (CLR), но обращается к члену, необходима упаковка.</span><span class="sxs-lookup"><span data-stu-id="4cb0e-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="4cb0e-104">*Упаковкой-преобразованием* называется обработка, необходимая для преобразования типа в `Object` или, в некоторых случаях, в <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="4cb0e-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="4cb0e-105">Среда CLR не поддерживает упаковку определенных типов структуры, например <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, и <xref:System.TypedReference>.</span><span class="sxs-lookup"><span data-stu-id="4cb0e-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="4cb0e-106">Это выражение пытается выполнить вызов метода, унаследованного от ограниченного типа <xref:System.Object> или <xref:System.ValueType>, такие как <xref:System.Object.GetHashCode%2A> или <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="4cb0e-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="4cb0e-107">Для доступа к этому методу, Visual Basic выполняется преобразование неявная упаковка-преобразование, которое вызывает эту ошибку.</span><span class="sxs-lookup"><span data-stu-id="4cb0e-107">To access this method, Visual Basic has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="4cb0e-108">**Идентификатор ошибки:** BC31393</span><span class="sxs-lookup"><span data-stu-id="4cb0e-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4cb0e-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="4cb0e-109">To correct this error</span></span>  
  
1. <span data-ttu-id="4cb0e-110">Найдите выражение, которое оценивается в указанный тип.</span><span class="sxs-lookup"><span data-stu-id="4cb0e-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2. <span data-ttu-id="4cb0e-111">Найдите часть инструкции, в которой предпринимается попытка вызова метода, унаследованного от <xref:System.Object> или <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="4cb0e-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3. <span data-ttu-id="4cb0e-112">Перепишите инструкцию, чтобы избежать вызова метода.</span><span class="sxs-lookup"><span data-stu-id="4cb0e-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cb0e-113">См. также</span><span class="sxs-lookup"><span data-stu-id="4cb0e-113">See also</span></span>

- [<span data-ttu-id="4cb0e-114">Явные и неявные преобразования</span><span class="sxs-lookup"><span data-stu-id="4cb0e-114">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
