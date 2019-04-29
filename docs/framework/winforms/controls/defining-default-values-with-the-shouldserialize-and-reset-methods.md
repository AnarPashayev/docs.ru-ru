---
title: Определение значений по умолчанию с помощью методов ShouldSerialize и Reset
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property methods
- ShouldPersist method
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
ms.openlocfilehash: f1f5a668c5d4f52ef7dd9f60a31c04f2173165f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972371"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="1f205-102">Определение значений по умолчанию с помощью методов ShouldSerialize и Reset</span><span class="sxs-lookup"><span data-stu-id="1f205-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="1f205-103">`ShouldSerialize` и `Reset` — необязательные методы, которые могут использоваться для свойства, в том случае, если свойство не имеет значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1f205-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="1f205-104">Если свойство имеет значение по умолчанию, необходимо применить <xref:System.ComponentModel.DefaultValueAttribute> и вместо этого укажите значение по умолчанию для конструктора класса атрибутов.</span><span class="sxs-lookup"><span data-stu-id="1f205-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="1f205-105">Любой из этих механизмов обеспечивает следующие возможности в конструкторе:</span><span class="sxs-lookup"><span data-stu-id="1f205-105">Either of these mechanisms enables the following features in the designer:</span></span>  
  
- <span data-ttu-id="1f205-106">Свойство предоставляет визуальную индикацию в обозревателе свойств, если он был изменен со значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1f205-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>  
  
- <span data-ttu-id="1f205-107">Пользователь может щелкнуть свойства и выберите **Сброс** восстановить значение свойства к значению по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1f205-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>  
  
- <span data-ttu-id="1f205-108">Конструктор создает более эффективный код.</span><span class="sxs-lookup"><span data-stu-id="1f205-108">The designer generates more efficient code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1f205-109">Либо применить <xref:System.ComponentModel.DefaultValueAttribute> или предоставить `Reset` *PropertyName* и `ShouldSerialize` *PropertyName* методы.</span><span class="sxs-lookup"><span data-stu-id="1f205-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="1f205-110">Не используйте их вместе.</span><span class="sxs-lookup"><span data-stu-id="1f205-110">Do not use both.</span></span>  
  
 <span data-ttu-id="1f205-111">`Reset` *PropertyName* метод задает свойство к значению по умолчанию, как показано в следующем фрагменте кода.</span><span class="sxs-lookup"><span data-stu-id="1f205-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>  
  
```vb  
Public Sub ResetMyFont()  
   MyFont = Nothing  
End Sub  
```  
  
```csharp  
public void ResetMyFont() {  
   MyFont = null;  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="1f205-112">Если свойство не является `Reset` метод, не помечен атрибутом <xref:System.ComponentModel.DefaultValueAttribute>и не имеет значения по умолчанию, указанного в его объявлении `Reset` для этого свойства отключен в контекстном меню **свойства** окна конструктора Windows Forms в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1f205-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in Visual Studio.</span></span>  
  
 <span data-ttu-id="1f205-113">Конструкторы, такой как Visual Studio используют `ShouldSerialize` *PropertyName* метод проверьте, изменено ли значение свойства по умолчанию и создание кода в форме, только если свойство изменяется, что позволяет более эффективный код поколение.</span><span class="sxs-lookup"><span data-stu-id="1f205-113">Designers such as Visual Studio use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="1f205-114">Пример:</span><span class="sxs-lookup"><span data-stu-id="1f205-114">For example:</span></span>  
  
```vb  
'Returns true if the font has changed; otherwise, returns false.  
' The designer writes code to the form only if true is returned.  
Public Function ShouldSerializeMyFont() As Boolean  
   Return Not (thefont Is Nothing)  
End Function  
```  
  
```csharp  
// Returns true if the font has changed; otherwise, returns false.  
// The designer writes code to the form only if true is returned.  
public bool ShouldSerializeMyFont() {  
   return thefont != null;  
}  
```  
  
 <span data-ttu-id="1f205-115">Полный пример кода ниже.</span><span class="sxs-lookup"><span data-stu-id="1f205-115">A complete code example follows.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
Imports System.Drawing  
  
Public Class MyControl  
   Inherits Control  
  
   ' Declare an instance of the Font class  
   ' and set its default value to Nothing.  
   Private thefont As Font = Nothing  
  
   ' The MyFont property.   
   Public Property MyFont() As Font  
      ' Note that the Font property never  
      ' returns null.  
      Get  
         If Not (thefont Is Nothing) Then  
            Return thefont  
         End If  
         If Not (Parent Is Nothing) Then  
            Return Parent.Font  
         End If  
         Return Control.DefaultFont  
      End Get  
      Set  
         thefont = value  
      End Set  
   End Property  
  
   Public Function ShouldSerializeMyFont() As Boolean  
      Return Not (thefont Is Nothing)  
   End Function  
  
   Public Sub ResetMyFont()  
      MyFont = Nothing  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Drawing;  
  
public class MyControl : Control {  
   // Declare an instance of the Font class  
   // and set its default value to null.  
   private Font thefont = null;  
  
   // The MyFont property.      
   public Font MyFont {  
      // Note that the MyFont property never  
      // returns null.  
      get {  
         if (thefont != null) return thefont;  
         if (Parent != null) return Parent.Font;  
         return Control.DefaultFont;  
      }  
      set {  
         thefont = value;  
      }  
   }  
  
   public bool ShouldSerializeMyFont() {  
      return thefont != null;  
   }  
  
   public void ResetMyFont() {  
      MyFont = null;  
   }  
}  
```  
  
 <span data-ttu-id="1f205-116">В данном случае, даже в том случае, если значение переменной закрытого обращается к `MyFont` свойство `null`, браузер свойств не отображается `null`; вместо этого он отображает <xref:System.Windows.Forms.Control.Font%2A> свойство родительского объекта, если это не `null`, или значение по умолчанию <xref:System.Windows.Forms.Control.Font%2A> значения, определенного в <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="1f205-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="1f205-117">Таким образом, значение по умолчанию для `MyFont` нельзя просто установить и <xref:System.ComponentModel.DefaultValueAttribute> не может использоваться для этого свойства.</span><span class="sxs-lookup"><span data-stu-id="1f205-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="1f205-118">Вместо этого `ShouldSerialize` и `Reset` методы должны быть реализованы для `MyFont` свойство.</span><span class="sxs-lookup"><span data-stu-id="1f205-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f205-119">См. также</span><span class="sxs-lookup"><span data-stu-id="1f205-119">See also</span></span>

- [<span data-ttu-id="1f205-120">Свойства элементов управления Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f205-120">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="1f205-121">Определение свойства</span><span class="sxs-lookup"><span data-stu-id="1f205-121">Defining a Property</span></span>](defining-a-property-in-windows-forms-controls.md)
- [<span data-ttu-id="1f205-122">События изменения свойств</span><span class="sxs-lookup"><span data-stu-id="1f205-122">Property-Changed Events</span></span>](property-changed-events.md)
