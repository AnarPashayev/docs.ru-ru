---
title: Практическое руководство. Восстановление часовых поясов из внедренного ресурса
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71fc4e04c87dfa3b83eabb06361d1da94a512a5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026540"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="769ae-102">Практическое руководство. Восстановление часовых поясов из внедренного ресурса</span><span class="sxs-lookup"><span data-stu-id="769ae-102">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="769ae-103">В этом разделе описывается восстановление часовых поясов, которые были сохранены в файле ресурсов.</span><span class="sxs-lookup"><span data-stu-id="769ae-103">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="769ae-104">Сведения и инструкции по сохранению часовых поясов см. в разделе [как: Сохранение часовых поясов во внедренном ресурсе](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span><span class="sxs-lookup"><span data-stu-id="769ae-104">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="769ae-105">Для десериализации объекта TimeZoneInfo из внедренного ресурса</span><span class="sxs-lookup"><span data-stu-id="769ae-105">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="769ae-106">Если часовой пояс извлекаемых не пользовательский часовой пояс, попытайтесь создать его экземпляр с помощью <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="769ae-106">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="769ae-107">Создать экземпляр <xref:System.Resources.ResourceManager> объекта, передав полное имя файла внедренного ресурса и ссылку на сборку, которая содержит файл ресурсов.</span><span class="sxs-lookup"><span data-stu-id="769ae-107">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="769ae-108">Если не удается определить полное имя файла внедренного ресурса, используйте [Ildasm.exe (дизассемблер IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) для проверки манифеста сборки.</span><span class="sxs-lookup"><span data-stu-id="769ae-108">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="769ae-109">`.mresource` Идентифицирует ресурс.</span><span class="sxs-lookup"><span data-stu-id="769ae-109">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="769ae-110">В примере, является полное имя ресурса `SerializeTimeZoneData.SerializedTimeZones`.</span><span class="sxs-lookup"><span data-stu-id="769ae-110">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="769ae-111">Если файл ресурсов внедряется в той же сборке, который содержит код создания экземпляра часового пояса, ссылку на него можно получить, вызвав `static` (`Shared` в Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="769ae-111">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="769ae-112">Если вызов <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> метод завершается ошибкой, или если экземпляр которой необходимо создать пользовательский часовой пояс, получить строка, содержащая сериализованный часовой пояс, вызвав <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> метод.</span><span class="sxs-lookup"><span data-stu-id="769ae-112">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="769ae-113">Десериализации данных часового пояса путем вызова <xref:System.TimeZoneInfo.FromSerializedString%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="769ae-113">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="769ae-114">Пример</span><span class="sxs-lookup"><span data-stu-id="769ae-114">Example</span></span>

<span data-ttu-id="769ae-115">В следующем примере десериализуется <xref:System.TimeZoneInfo> объект, хранящийся во внедренном файле ресурсов .NET XML.</span><span class="sxs-lookup"><span data-stu-id="769ae-115">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="769ae-116">Этот код иллюстрирует обработку исключений, чтобы убедиться, что <xref:System.TimeZoneInfo> присутствует объект, необходимый для приложения.</span><span class="sxs-lookup"><span data-stu-id="769ae-116">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="769ae-117">Сначала выполняется попытка создать экземпляр <xref:System.TimeZoneInfo> путем извлечения его из реестра с помощью <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="769ae-117">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="769ae-118">Если часовой пояс не может быть создан, код получает его из файла внедренных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="769ae-118">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="769ae-119">Так как данные для пользовательских часовых поясов (часовых поясов, созданных с помощью <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> метод) не хранятся в реестре, код не вызывает <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> для создания экземпляра часового пояса Антарктики.</span><span class="sxs-lookup"><span data-stu-id="769ae-119">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="769ae-120">Вместо этого он немедленно проверяет файл внедренных ресурсов для получения строки, которая содержит данные о часовом поясе, перед вызовом <xref:System.TimeZoneInfo.FromSerializedString%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="769ae-120">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="769ae-121">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="769ae-121">Compiling the code</span></span>

<span data-ttu-id="769ae-122">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="769ae-122">This example requires:</span></span>

* <span data-ttu-id="769ae-123">Чтобы добавить в проект ссылку на System.Windows.Forms.dll и System.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="769ae-123">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="769ae-124">Что импортируется следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="769ae-124">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="769ae-125">См. также</span><span class="sxs-lookup"><span data-stu-id="769ae-125">See also</span></span>

- [<span data-ttu-id="769ae-126">Даты, время и часовые пояса</span><span class="sxs-lookup"><span data-stu-id="769ae-126">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="769ae-127">Общие сведения о часовых поясах</span><span class="sxs-lookup"><span data-stu-id="769ae-127">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
- [<span data-ttu-id="769ae-128">Практическое руководство. Сохранение часовых поясов во внедренном ресурсе</span><span class="sxs-lookup"><span data-stu-id="769ae-128">How to: Save time zones to an embedded resource</span></span>](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
