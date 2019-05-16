---
title: Сериализация в .NET
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 1f90a128ef6b29acbd315beae7aaaf1d1b78a62b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638848"
---
# <a name="serialization-in-net"></a><span data-ttu-id="06bcc-102">Сериализация в .NET</span><span class="sxs-lookup"><span data-stu-id="06bcc-102">Serialization in .NET</span></span>
<span data-ttu-id="06bcc-103">Сериализация представляет собой процесс преобразования состояния объекта в форму, пригодную для сохранения или передачи.</span><span class="sxs-lookup"><span data-stu-id="06bcc-103">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="06bcc-104">Дополнением к сериализации служит десериализация, при которой осуществляется преобразование потока в объект.</span><span class="sxs-lookup"><span data-stu-id="06bcc-104">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="06bcc-105">Вместе они обеспечивают простое хранение и передачу данных.</span><span class="sxs-lookup"><span data-stu-id="06bcc-105">Together, these processes allow data to be easily stored and transferred.</span></span>  
  
<span data-ttu-id="06bcc-106">В .NET доступны две технологии сериализации.</span><span class="sxs-lookup"><span data-stu-id="06bcc-106">.NET features two serialization technologies:</span></span>  
  
- <span data-ttu-id="06bcc-107">При двоичной сериализации сохраняется правильность типов, что полезно для сохранения состояния объекта между разными вызовами приложения.</span><span class="sxs-lookup"><span data-stu-id="06bcc-107">Binary serialization preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="06bcc-108">Например, можно обеспечить совместный доступ к объекту для разных приложений, сериализовав его в буфер обмена.</span><span class="sxs-lookup"><span data-stu-id="06bcc-108">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="06bcc-109">Объект можно сериализовать в поток, на диск, в память, передать по сети и т. д.</span><span class="sxs-lookup"><span data-stu-id="06bcc-109">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="06bcc-110">При удаленном управлении сериализация используется для передачи объектов "по значению" с одного компьютера или домена приложения на другой.</span><span class="sxs-lookup"><span data-stu-id="06bcc-110">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
- <span data-ttu-id="06bcc-111">При XML-сериализации сериализуются только открытые свойства и поля, а правильность типов не сохраняется.</span><span class="sxs-lookup"><span data-stu-id="06bcc-111">XML serialization serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="06bcc-112">Этот метод полезен для предоставления или использования данных без ограничений работающего с ними приложения.</span><span class="sxs-lookup"><span data-stu-id="06bcc-112">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="06bcc-113">Будучи открытым стандартом, XML привлекателен для совместного использования данных в Интернете.</span><span class="sxs-lookup"><span data-stu-id="06bcc-113">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="06bcc-114">Аналогичным образом и SOAP представляет собой открытый стандарт, использование которого эффективно и удобно.</span><span class="sxs-lookup"><span data-stu-id="06bcc-114">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="06bcc-115">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="06bcc-115">In This Section</span></span>  
[<span data-ttu-id="06bcc-116">Практические руководства по сериализации</span><span class="sxs-lookup"><span data-stu-id="06bcc-116">Serialization How-to Topics</span></span>](../../../docs/standard/serialization/serialization-how-to-topics.md)  
<span data-ttu-id="06bcc-117">Ссылки на подразделы "Практическое руководство" данного раздела.</span><span class="sxs-lookup"><span data-stu-id="06bcc-117">Lists links to How-to topics contained in this section.</span></span>
  
[<span data-ttu-id="06bcc-118">Двоичная сериализация</span><span class="sxs-lookup"><span data-stu-id="06bcc-118">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
<span data-ttu-id="06bcc-119">Описывает механизм двоичной сериализации, входящий в среду CLR.</span><span class="sxs-lookup"><span data-stu-id="06bcc-119">Describes the binary serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="06bcc-120">Сериализация XML и SOAP</span><span class="sxs-lookup"><span data-stu-id="06bcc-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
<span data-ttu-id="06bcc-121">Описывает механизм сериализации XML и SOAP, входящий в среду CLR.</span><span class="sxs-lookup"><span data-stu-id="06bcc-121">Describes the XML and SOAP serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="06bcc-122">Инструменты сериализации</span><span class="sxs-lookup"><span data-stu-id="06bcc-122">Serialization Tools</span></span>](../../../docs/standard/serialization/serialization-tools.md)  
<span data-ttu-id="06bcc-123">Эти средства упрощают разработку кода сериализации.</span><span class="sxs-lookup"><span data-stu-id="06bcc-123">These tools help develop serialization code.</span></span>

[<span data-ttu-id="06bcc-124">Образцы сериализации</span><span class="sxs-lookup"><span data-stu-id="06bcc-124">Serialization Samples</span></span>](../../../docs/standard/serialization/serialization-samples.md)  
<span data-ttu-id="06bcc-125">Выполнение сериализации показано в образцах.</span><span class="sxs-lookup"><span data-stu-id="06bcc-125">The samples demonstrate how to do serialization.</span></span>

## <a name="reference"></a><span data-ttu-id="06bcc-126">Ссылка</span><span class="sxs-lookup"><span data-stu-id="06bcc-126">Reference</span></span>
<span data-ttu-id="06bcc-127"><xref:System.Runtime.Serialization> Содержит классы, которые можно использовать для сериализации и десериализации объектов.</span><span class="sxs-lookup"><span data-stu-id="06bcc-127"><xref:System.Runtime.Serialization> Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="06bcc-128">Содержит классы, которые можно использовать для сериализации объектов в документы формата XML или в потоки.</span><span class="sxs-lookup"><span data-stu-id="06bcc-128">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>
