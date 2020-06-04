---
title: Методы System.Nullable(Of T) нельзя использовать в качестве операндов оператора AddressOf
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 61c6fe7c33b3292066e653304ded43a863413723
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397224"
---
# <a name="methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a>Методы System.Nullable(Of T) нельзя использовать в качестве операндов оператора AddressOf
Оператор использует `AddressOf` оператор с операндом, представляющим процедуру <xref:System.Nullable%601> структуры.  
  
 **Идентификатор ошибки:** BC32126  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Замените имя процедуры в `AddressOf` предложении операндом, который не является членом <xref:System.Nullable%601> .  
  
- Напишите класс, который заключает в оболочку метод <xref:System.Nullable%601> , который требуется использовать. В следующем примере `NullableWrapper` класс определяет новый метод с именем `GetValueOrDefault` . Поскольку этот новый метод не является членом <xref:System.Nullable%601> , он может быть применен к `nullInstance` экземпляру типа, допускающему значение null, для формирования аргумента для `AddressOf` .  
  
```vb  
Module Module1  
  
    Delegate Function Deleg() As Integer  
  
    Sub Main()  
        Dim nullInstance As New Nullable(Of Integer)(1)  
  
        Dim del As Deleg  
  
        ' GetValueOrDefault is a method of the Nullable generic  
        ' type. It cannot be used as an operand of AddressOf.  
        ' del = AddressOf nullInstance.GetValueOrDefault  
  
        ' The following line uses the GetValueOrDefault method  
        ' defined in the NullableWrapper class.  
        del = AddressOf (New NullableWrapper(  
            Of Integer)(nullInstance)).GetValueOrDefault  
  
        Console.WriteLine(del.Invoke())  
    End Sub  
  
    Class NullableWrapper(Of T As Structure)  
        Private m_Value As Nullable(Of T)  
  
        Sub New(ByVal Value As Nullable(Of T))  
            m_Value = Value  
        End Sub  
  
        Public Function GetValueOrDefault() As T  
            Return m_Value.Value  
        End Function  
    End Class  
End Module  
```  
  
## <a name="see-also"></a>См. также раздел

- <xref:System.Nullable%601>
- [Оператор AddressOf](../operators/addressof-operator.md)
- [Типы значений, допускающие значение null](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
