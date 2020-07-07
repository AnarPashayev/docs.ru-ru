---
title: Практическое руководство. Создание сборок взаимодействия из библиотек типов
description: Создайте сборки взаимодействия из библиотек типов. Используйте программу импорта библиотек типов (Tlbimp.exe) для преобразования коклассов и интерфейсов из библиотеки типов COM в метаданные.
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
ms.openlocfilehash: 6f54875d6aadb1da18cf25a1bec0a0e451f4a24c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619563"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="c59fc-104">Практическое руководство. Создание сборок взаимодействия из библиотек типов</span><span class="sxs-lookup"><span data-stu-id="c59fc-104">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="c59fc-105">[Программа импорта библиотек типов (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) — это средство командной строки, которое преобразует коклассы и интерфейсы, содержащиеся в библиотеке типов COM, в метаданные.</span><span class="sxs-lookup"><span data-stu-id="c59fc-105">The [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="c59fc-106">Это средство автоматически создает сборку взаимодействия и пространство имен для сведений о типе.</span><span class="sxs-lookup"><span data-stu-id="c59fc-106">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="c59fc-107">После того как метаданные класса стали доступными, управляемые клиенты могут создавать экземпляры типа COM и вызывать его методы, как если бы это был экземпляр .NET.</span><span class="sxs-lookup"><span data-stu-id="c59fc-107">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="c59fc-108">Средство Tlbimp.exe преобразует всю библиотеку типов в метаданные за один раз и не может создать сведения о типах для подмножества типов, определенных в библиотеке типов.</span><span class="sxs-lookup"><span data-stu-id="c59fc-108">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="c59fc-109">Создание сборки взаимодействия из библиотеки типов</span><span class="sxs-lookup"><span data-stu-id="c59fc-109">To generate an interop assembly from a type library</span></span>  
  
1. <span data-ttu-id="c59fc-110">Используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="c59fc-110">Use the following command:</span></span>  
  
     <span data-ttu-id="c59fc-111">**tlbimp** \<*type-library-file*></span><span class="sxs-lookup"><span data-stu-id="c59fc-111">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="c59fc-112">При указании параметра **/out:** создается сборка взаимодействия с измененным именем, например LOANLib.dll.</span><span class="sxs-lookup"><span data-stu-id="c59fc-112">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="c59fc-113">Изменение имени сборки взаимодействия помогает отличить эту сборку от исходного файла DLL COM и избежать возможных проблем с повторяющимися именами.</span><span class="sxs-lookup"><span data-stu-id="c59fc-113">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c59fc-114">Пример</span><span class="sxs-lookup"><span data-stu-id="c59fc-114">Example</span></span>  
 <span data-ttu-id="c59fc-115">Следующая команда создает сборку Loanlib.dll в пространстве имен `Loanlib`.</span><span class="sxs-lookup"><span data-stu-id="c59fc-115">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```console  
tlbimp Loanlib.tlb  
```  
  
 <span data-ttu-id="c59fc-116">Следующая команда создает сборку взаимодействия с измененным именем (LOANLib.dll).</span><span class="sxs-lookup"><span data-stu-id="c59fc-116">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```console  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="c59fc-117">См. также</span><span class="sxs-lookup"><span data-stu-id="c59fc-117">See also</span></span>

- [<span data-ttu-id="c59fc-118">Импорт библиотеки типов в виде сборки</span><span class="sxs-lookup"><span data-stu-id="c59fc-118">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="c59fc-119">Предоставление COM-компонентов платформе .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c59fc-119">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
