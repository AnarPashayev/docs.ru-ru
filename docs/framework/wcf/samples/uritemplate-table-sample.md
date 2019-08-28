---
title: Пример таблицы UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: 9d60de39c8c025b31c45c79309442906fc3aab4e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044575"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="73d19-102">Пример таблицы UriTemplate</span><span class="sxs-lookup"><span data-stu-id="73d19-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="73d19-103">Класс <xref:System.UriTemplateTable> предоставляет структуру ассоциативной таблицы, подобную словарю, для работы с набором экземпляров `UriTemplate`.</span><span class="sxs-lookup"><span data-stu-id="73d19-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="73d19-104">Конкретные универсальные коды ресурса (URI) могут эффективно сравниваться со всеми шаблонами в таблице, после чего могут извлекаться данные, связанные с совпадающим шаблоном.</span><span class="sxs-lookup"><span data-stu-id="73d19-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="73d19-105">Данный пример демонстрирует следующие ключевые понятия, связанные с классом `UriTemplateTable`:</span><span class="sxs-lookup"><span data-stu-id="73d19-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="73d19-106">Синтаксис для создания экземпляров `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="73d19-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="73d19-107">Занесение в `UriTemplateTable` набора пар ключ/значение.</span><span class="sxs-lookup"><span data-stu-id="73d19-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
- <span data-ttu-id="73d19-108">Сравнение потенциального универсального кода ресурса (URI) по таблице с использованием <xref:System.UriTemplateTable.MatchSingle%2A>.</span><span class="sxs-lookup"><span data-stu-id="73d19-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="73d19-109">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="73d19-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="73d19-110">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73d19-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="73d19-111">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="73d19-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="73d19-112">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="73d19-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="73d19-113">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="73d19-113">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="73d19-114">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , чтобы скачать все Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] и примеры.</span><span class="sxs-lookup"><span data-stu-id="73d19-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="73d19-115">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="73d19-115">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="73d19-116">См. также</span><span class="sxs-lookup"><span data-stu-id="73d19-116">See also</span></span>

- [<span data-ttu-id="73d19-117">Диспетчер таблицы UriTemplate</span><span class="sxs-lookup"><span data-stu-id="73d19-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [<span data-ttu-id="73d19-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="73d19-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
