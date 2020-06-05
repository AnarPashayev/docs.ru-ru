---
title: Имя <namespacename> в корневом пространстве имен <fullnamespacename> не является CLS-совместимым
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: b03a50365122c17fa311a284bd6995d1af2631c3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401541"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a><span data-ttu-id="257fd-102">Имя \<namespacename> в корневом пространстве имен \<fullnamespacename> не является CLS-совместимым</span><span class="sxs-lookup"><span data-stu-id="257fd-102">Name \<namespacename> in the root namespace \<fullnamespacename> is not CLS-compliant</span></span>
<span data-ttu-id="257fd-103">Сборка помечена как `<CLSCompliant(True)>` , но элемент имени корневого пространства имен начинается с символа подчеркивания ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="257fd-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="257fd-104">Программный элемент может содержать один или несколько символов подчеркивания, но для соответствия [языковым независимостьм и зависимым от языка компонентам](../../../standard/language-independence-and-language-independent-components.md) (CLS) он не должен начинаться с символа подчеркивания.</span><span class="sxs-lookup"><span data-stu-id="257fd-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="257fd-105">См. раздел [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="257fd-105">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="257fd-106">При применении атрибута <xref:System.CLSCompliantAttribute> к программному элементу вы задаете для параметра `isCompliant` атрибута значение `True` или `False` , чтобы указать совместимость или несовместимость.</span><span class="sxs-lookup"><span data-stu-id="257fd-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="257fd-107">Для этого параметра нет значения по умолчанию, и вы должны предоставить значение.</span><span class="sxs-lookup"><span data-stu-id="257fd-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="257fd-108">Если вы не применяете <xref:System.CLSCompliantAttribute> к элементу, он считается несовместимым.</span><span class="sxs-lookup"><span data-stu-id="257fd-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="257fd-109">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="257fd-109">By default, this message is a warning.</span></span> <span data-ttu-id="257fd-110">Сведения о сокрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="257fd-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="257fd-111">**Идентификатор ошибки:** BC40039</span><span class="sxs-lookup"><span data-stu-id="257fd-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="257fd-112">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="257fd-112">To correct this error</span></span>  
  
- <span data-ttu-id="257fd-113">Если требуется совместимость с CLS, измените имя корневого пространства имен так, чтобы ни один из его элементов не начинался с символа подчеркивания.</span><span class="sxs-lookup"><span data-stu-id="257fd-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
- <span data-ttu-id="257fd-114">Если требуется, чтобы имя пространства имен оставалось без изменений, удалите <xref:System.CLSCompliantAttribute> из сборки или пометьте его как `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="257fd-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="257fd-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="257fd-115">See also</span></span>

- [<span data-ttu-id="257fd-116">Оператор Namespace</span><span class="sxs-lookup"><span data-stu-id="257fd-116">Namespace Statement</span></span>](../statements/namespace-statement.md)
- [<span data-ttu-id="257fd-117">Пространства имен в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="257fd-117">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="257fd-118">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="257fd-118">-rootnamespace</span></span>](../../reference/command-line-compiler/rootnamespace.md)
- [<span data-ttu-id="257fd-119">Страница "Приложение" в конструкторе проектов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="257fd-119">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="257fd-120">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="257fd-120">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="257fd-121">Соглашения об именах Visual Basic</span><span class="sxs-lookup"><span data-stu-id="257fd-121">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
