---
title: Юникод
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: 2f415e70e6ffb5295d49c919383462b9f726f88a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867664"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="b6e9a-102">Юникод (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6e9a-102">Unicode (Visual Basic)</span></span>

<span data-ttu-id="b6e9a-103">Указывает, что Visual Basic должны маршалировать все строки в значения Юникода независимо от имени объявляемой внешней процедуры.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="b6e9a-104">При вызове процедуры, определенной вне проекта, Visual Basic компилятор не имеет доступа к информации, которая необходима для правильного вызова процедуры.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="b6e9a-105">Эти сведения включают в себя расположение процедуры, способ ее определения, последовательность вызова и тип возвращаемого значения, а также используемую строковую кодировку.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="b6e9a-106">[Инструкция DECLARE](../statements/declare-statement.md) создает ссылку на внешнюю процедуру и предоставляет эти необходимые сведения.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-106">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="b6e9a-107">`charsetmodifier`Часть в `Declare` инструкции предоставляет сведения о кодировке для маршалирования строк во время вызова внешней процедуры.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="b6e9a-108">Он также влияет на то, как Visual Basic ищет имя внешней процедуры во внешнем файле.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="b6e9a-109">`Unicode`Модификатор указывает, что Visual Basic должен маршалировать все строки в значения Юникода и выполнять поиск процедуры, не изменяя ее имя во время поиска.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="b6e9a-110">Если модификатор кодировки не указан, используется значение `Ansi` по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6e9a-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="b6e9a-111">Remarks</span></span>  

 <span data-ttu-id="b6e9a-112">`Unicode`Модификатор можно использовать в этом контексте:</span><span class="sxs-lookup"><span data-stu-id="b6e9a-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="b6e9a-113">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="b6e9a-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="b6e9a-114">Примечания для разработчиков смарт-устройств</span><span class="sxs-lookup"><span data-stu-id="b6e9a-114">Smart Device Developer Notes</span></span>  

 <span data-ttu-id="b6e9a-115">Это ключевое слово не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="b6e9a-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e9a-116">См. также</span><span class="sxs-lookup"><span data-stu-id="b6e9a-116">See also</span></span>

- [<span data-ttu-id="b6e9a-117">Набора</span><span class="sxs-lookup"><span data-stu-id="b6e9a-117">Ansi</span></span>](ansi.md)
- [<span data-ttu-id="b6e9a-118">Автоматически</span><span class="sxs-lookup"><span data-stu-id="b6e9a-118">Auto</span></span>](auto.md)
- [<span data-ttu-id="b6e9a-119">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="b6e9a-119">Keywords</span></span>](../keywords/index.md)
