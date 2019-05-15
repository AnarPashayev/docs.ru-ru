---
title: Практическое руководство. Руководство по программированию на C#. Использование псевдонима глобального пространства имен
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: 6d3e0740a472f74116712e737e49f86d4202dea5
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452801"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a><span data-ttu-id="ef2fa-102">Практическое руководство. Руководство по программированию на C#. Использование псевдонима глобального пространства имен</span><span class="sxs-lookup"><span data-stu-id="ef2fa-102">How to: Use the Global Namespace Alias (C# Programming Guide)</span></span>
<span data-ttu-id="ef2fa-103">Возможность доступа к члену в глобальном [пространстве имен](../../../csharp/language-reference/keywords/namespace.md) полезна в тех случаях, когда член может быть скрыт другой сущностью с таким же именем.</span><span class="sxs-lookup"><span data-stu-id="ef2fa-103">The ability to access a member in the global [namespace](../../../csharp/language-reference/keywords/namespace.md) is useful when the member might be hidden by another entity of the same name.</span></span>  
  
 <span data-ttu-id="ef2fa-104">Например, в следующем коде `Console` разрешается в `TestApp.Console` вместо типа `Console` в пространстве имен <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="ef2fa-104">For example, in the following code, `Console` resolves to `TestApp.Console` instead of to the `Console` type in the <xref:System> namespace.</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuideNamespaces#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#1)]  
  
 <span data-ttu-id="ef2fa-105">При использовании `System.Console` по-прежнему возникает ошибка, поскольку пространство имен `System` скрыто классом `TestApp.System`:</span><span class="sxs-lookup"><span data-stu-id="ef2fa-105">Using `System.Console` still results in an error because the `System` namespace is hidden by the class `TestApp.System`:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#2)]  
  
 <span data-ttu-id="ef2fa-106">Тем не менее эту ошибку можно обойти с помощью `global::System.Console`, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="ef2fa-106">However, you can work around this error by using `global::System.Console`, like this:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#3)]  
  
 <span data-ttu-id="ef2fa-107">Если левый идентификатор равен `global`, поиск правого идентификатора начинается с глобального пространства имен.</span><span class="sxs-lookup"><span data-stu-id="ef2fa-107">When the left identifier is `global`, the search for the right identifier starts at the global namespace.</span></span> <span data-ttu-id="ef2fa-108">Например, следующее объявление ссылается на `TestApp` как на член глобального пространства имен.</span><span class="sxs-lookup"><span data-stu-id="ef2fa-108">For example, the following declaration is referencing `TestApp` as a member of the global space.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#4)]  
  
 <span data-ttu-id="ef2fa-109">Очевидно, создавать собственные пространства имен с названием `System` не рекомендуется, и вряд ли вам когда-нибудь попадется код, где это сделано.</span><span class="sxs-lookup"><span data-stu-id="ef2fa-109">Obviously, creating your own namespaces called `System` is not recommended, and it is unlikely you will encounter any code in which this has happened.</span></span> <span data-ttu-id="ef2fa-110">Тем не менее в крупных проектах существует вполне реальная вероятность того, что названия пространств имен будут в той или иной форме дублироваться.</span><span class="sxs-lookup"><span data-stu-id="ef2fa-110">However, in larger projects, it is a very real possibility that namespace duplication may occur in one form or another.</span></span> <span data-ttu-id="ef2fa-111">В таких ситуациях вы можете гарантировать использование корневого пространства имен, указав квалификатор пространства имен global.</span><span class="sxs-lookup"><span data-stu-id="ef2fa-111">In these situations, the global namespace qualifier is your guarantee that you can specify the root namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef2fa-112">Пример</span><span class="sxs-lookup"><span data-stu-id="ef2fa-112">Example</span></span>  
 <span data-ttu-id="ef2fa-113">В этом примере пространство имен `System` используется для включения класса `TestClass`. Таким образом, следует использовать `global::System.Console` для ссылки на класс `System.Console`, который скрыт пространством имен `System`.</span><span class="sxs-lookup"><span data-stu-id="ef2fa-113">In this example, the namespace `System` is used to include the class `TestClass` therefore, `global::System.Console` must be used to reference the `System.Console` class, which is hidden by the `System` namespace.</span></span> <span data-ttu-id="ef2fa-114">Также используется псевдоним `colAlias` для ссылки на пространство имен `System.Collections`. Таким образом, экземпляр <xref:System.Collections.Hashtable?displayProperty=nameWithType> был создан с использованием этого псевдонима вместо пространства имен.</span><span class="sxs-lookup"><span data-stu-id="ef2fa-114">Also, the alias `colAlias` is used to refer to the namespace `System.Collections`; therefore, the instance of a <xref:System.Collections.Hashtable?displayProperty=nameWithType> was created using this alias instead of the namespace.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]  
  
<span data-ttu-id="ef2fa-115">**A 1**
**B 2**
**C 3**</span><span class="sxs-lookup"><span data-stu-id="ef2fa-115">**A 1**
**B 2**
**C 3**</span></span>

## <a name="see-also"></a><span data-ttu-id="ef2fa-116">См. также</span><span class="sxs-lookup"><span data-stu-id="ef2fa-116">See also</span></span>

- [<span data-ttu-id="ef2fa-117">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="ef2fa-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ef2fa-118">Пространства имен</span><span class="sxs-lookup"><span data-stu-id="ef2fa-118">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="ef2fa-119">:: Оператор</span><span class="sxs-lookup"><span data-stu-id="ef2fa-119">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)
- [<span data-ttu-id="ef2fa-120">extern</span><span class="sxs-lookup"><span data-stu-id="ef2fa-120">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
