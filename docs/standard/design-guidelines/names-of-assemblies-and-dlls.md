---
title: Имена сборок и библиотек DLL
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
author: KrzysztofCwalina
ms.openlocfilehash: 1aeef9e1be6e5fe747f440a8cb7f21095cb22f49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945500"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="81bf0-102">Имена сборок и библиотек DLL</span><span class="sxs-lookup"><span data-stu-id="81bf0-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="81bf0-103">Сборка является единицей развертывания и удостоверение для управляемого кода программы.</span><span class="sxs-lookup"><span data-stu-id="81bf0-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="81bf0-104">Несмотря на то, что сборки могут охватывать один или несколько файлов, обычно сборки взаимно-однозначное сопоставление с библиотекой DLL.</span><span class="sxs-lookup"><span data-stu-id="81bf0-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="81bf0-105">Таким образом в этом разделе описывается только DLL соглашения об именовании, которые затем можно сопоставить с соглашения об именовании сборок.</span><span class="sxs-lookup"><span data-stu-id="81bf0-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>  
  
 <span data-ttu-id="81bf0-106">**✓ DO** выбирать имена DLL-библиотек, указывающие на больших объемов функциональные возможности, например System.Data сборки.</span><span class="sxs-lookup"><span data-stu-id="81bf0-106">**✓ DO** choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>  
  
 <span data-ttu-id="81bf0-107">Имена сборки и библиотеки DLL не обязательно должны соответствовать имена пространств имен, но следует за именем пространства имен, при именовании сборок.</span><span class="sxs-lookup"><span data-stu-id="81bf0-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="81bf0-108">Хорошее проверенное правило — это имя библиотеки DLL, в соответствии с общим префиксом пространства имен, содержащиеся в сборке.</span><span class="sxs-lookup"><span data-stu-id="81bf0-108">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="81bf0-109">Например, сборки с двумя пространствами имен `MyCompany.MyTechnology.FirstFeature` и `MyCompany.MyTechnology.SecondFeature`, можно вызвать `MyCompany.MyTechnology.dll`.</span><span class="sxs-lookup"><span data-stu-id="81bf0-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>  
  
 <span data-ttu-id="81bf0-110">**✓ CONSIDER** об именовании библиотек DLL по следующему шаблону:</span><span class="sxs-lookup"><span data-stu-id="81bf0-110">**✓ CONSIDER** naming DLLs according to the following pattern:</span></span>  
  
 `<Company>.<Component>.dll`  
  
 <span data-ttu-id="81bf0-111">где `<Component>` содержит один или несколько предложений, разделенные точками.</span><span class="sxs-lookup"><span data-stu-id="81bf0-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="81bf0-112">Пример:</span><span class="sxs-lookup"><span data-stu-id="81bf0-112">For example:</span></span>  
  
 <span data-ttu-id="81bf0-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="81bf0-113">`Litware.Controls.dll`.</span></span>  
  
 <span data-ttu-id="81bf0-114">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="81bf0-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="81bf0-115">*Перепечатано разрешением Пирсона для образовательных учреждений, Inc. из [рекомендации по разработке Framework: Условные обозначения, стили и шаблоны для библиотеки .NET для повторного использования, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Кшиштов Квалина и Брэд Абрамс, опубликованных 22 октября 2008 г., издательство Addison-Wesley Professional как части цикла разработки Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="81bf0-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81bf0-116">См. также</span><span class="sxs-lookup"><span data-stu-id="81bf0-116">See also</span></span>

- [<span data-ttu-id="81bf0-117">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="81bf0-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="81bf0-118">Правила именования</span><span class="sxs-lookup"><span data-stu-id="81bf0-118">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
