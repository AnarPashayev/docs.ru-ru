---
title: 'При доступе к свойству по умолчанию возникает неоднозначность между членами наследуемых интерфейсов: <defaultpropertyname> интерфейса <interfacename1> и <defaultpropertyname> интерфейса <interfacename2>'
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: 99d5dc2e0f8389f8c9e90786c4d9d0fa037eb828
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651421"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a><span data-ttu-id="c8125-102">Доступ к свойству по умолчанию определяется неоднозначно между членами наследуемых интерфейсов\<defaultpropertyname > "интерфейса"\<имя_интерфейса1 > "и"\<defaultpropertyname > "интерфейса"\< имя_интерфейса2 > "</span><span class="sxs-lookup"><span data-stu-id="c8125-102">Default property access is ambiguous between the inherited interface members '\<defaultpropertyname>' of interface '\<interfacename1>' and '\<defaultpropertyname>' of interface '\<interfacename2>'</span></span>
<span data-ttu-id="c8125-103">Интерфейс наследует от двух интерфейсов, каждый из которых объявляет свойство по умолчанию с тем же именем.</span><span class="sxs-lookup"><span data-stu-id="c8125-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="c8125-104">Компилятор не может разрешить доступ к этому свойству значение по умолчанию без указания полного имени.</span><span class="sxs-lookup"><span data-stu-id="c8125-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="c8125-105">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c8125-105">The following example illustrates this.</span></span>  
  
```  
Public Interface Iface1  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface2  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface3  
    Inherits Iface1, Iface2  
End Interface  
Public Class testClass  
    Public Sub accessDefaultProperty()  
        Dim testObj As Iface3  
        Dim testInt As Integer = testObj(1)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="c8125-106">При указании `testObj(1)`, компилятор пытается разрешить его в свойство по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c8125-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="c8125-107">Тем не менее существуют два свойства по умолчанию из-за наследуемых интерфейсов, поэтому компилятор создает эту ошибку.</span><span class="sxs-lookup"><span data-stu-id="c8125-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>  
  
 <span data-ttu-id="c8125-108">**Идентификатор ошибки:** BC30686</span><span class="sxs-lookup"><span data-stu-id="c8125-108">**Error ID:** BC30686</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c8125-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="c8125-109">To correct this error</span></span>  
  
- <span data-ttu-id="c8125-110">Избегайте наследования элементов с одинаковым именем.</span><span class="sxs-lookup"><span data-stu-id="c8125-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="c8125-111">В предыдущем примере если `testObj` не требуется ни один из членов, скажем, `Iface2`, объявите ее следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c8125-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     <span data-ttu-id="c8125-112">-или-</span><span class="sxs-lookup"><span data-stu-id="c8125-112">-or-</span></span>  
  
- <span data-ttu-id="c8125-113">Реализуйте наследуемый интерфейс в классе.</span><span class="sxs-lookup"><span data-stu-id="c8125-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="c8125-114">Затем можно реализовать все наследуемые свойства с разными именами.</span><span class="sxs-lookup"><span data-stu-id="c8125-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="c8125-115">Однако только один из них может быть свойство по умолчанию, реализующего класса.</span><span class="sxs-lookup"><span data-stu-id="c8125-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="c8125-116">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c8125-116">The following example illustrates this.</span></span>  
  
    ```  
    Public Class useIface3  
        Implements Iface3  
        Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop  
            ' Insert code to define Get and Set procedures for prop1.  
        End Property  
        Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop  
            ' Insert code to define Get and Set procedures for prop2.  
        End Property  
    End Class  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c8125-117">См. также</span><span class="sxs-lookup"><span data-stu-id="c8125-117">See also</span></span>

- [<span data-ttu-id="c8125-118">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="c8125-118">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
