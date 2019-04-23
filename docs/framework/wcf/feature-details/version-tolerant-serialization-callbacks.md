---
title: Обратные вызовы сериализации, независимые от версий
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OnDeserializedAttribute [WCF]
- OnDeserializingAttribute [WCF]
- OnSerializingAttribute [WCF]
- serialization [WCF], setting default values
- OnSerializedAttribute [WCF]
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
ms.openlocfilehash: da13f9989b427da047c4a94f77907847ed2ae4d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124635"
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="9dc44-102">Обратные вызовы сериализации, независимые от версий</span><span class="sxs-lookup"><span data-stu-id="9dc44-102">Version-Tolerant Serialization Callbacks</span></span>
<span data-ttu-id="9dc44-103">Модель программирования контракта данных полностью поддерживает методы обратных вызовов независимой от версий сериализации, которые в свою очередь поддерживают классы <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> и <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span><span class="sxs-lookup"><span data-stu-id="9dc44-103">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="9dc44-104">Атрибуты независимой от версий сериализации</span><span class="sxs-lookup"><span data-stu-id="9dc44-104">Version-Tolerant Attributes</span></span>  
 <span data-ttu-id="9dc44-105">Существует четыре атрибута обратных вызовов.</span><span class="sxs-lookup"><span data-stu-id="9dc44-105">There are four callback attributes.</span></span> <span data-ttu-id="9dc44-106">Каждый атрибут можно применить к методу, который вызывает ядро сериализации/десериализации в те или иные моменты времени.</span><span class="sxs-lookup"><span data-stu-id="9dc44-106">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="9dc44-107">В таблице ниже представлены правила использования каждого атрибута.</span><span class="sxs-lookup"><span data-stu-id="9dc44-107">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="9dc44-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="9dc44-108">Attribute</span></span>|<span data-ttu-id="9dc44-109">Когда вызывается соответствующий метод</span><span class="sxs-lookup"><span data-stu-id="9dc44-109">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="9dc44-110">Вызывается перед сериализацией типа.</span><span class="sxs-lookup"><span data-stu-id="9dc44-110">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="9dc44-111">Вызывается после сериализации типа.</span><span class="sxs-lookup"><span data-stu-id="9dc44-111">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="9dc44-112">Вызывается перед десериализацией типа.</span><span class="sxs-lookup"><span data-stu-id="9dc44-112">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="9dc44-113">Вызывается после десериализации типа.</span><span class="sxs-lookup"><span data-stu-id="9dc44-113">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="9dc44-114">Методы должны принимать параметр <xref:System.Runtime.Serialization.StreamingContext>.</span><span class="sxs-lookup"><span data-stu-id="9dc44-114">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="9dc44-115">Эти методы в первую очередь предназначены для использования с управлением версиями или инициализацией.</span><span class="sxs-lookup"><span data-stu-id="9dc44-115">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="9dc44-116">Во время десериализации конструкторы не вызываются.</span><span class="sxs-lookup"><span data-stu-id="9dc44-116">During deserialization, no constructors are called.</span></span> <span data-ttu-id="9dc44-117">Поэтому возможна некорректная инициализация элементов данных (согласно заданным значениям по умолчанию), если данные для этих элементов отсутствуют во входящем потоке, например, если данные поступают из предыдущей версии типа, в котором отсутствуют некоторые элементы данных.</span><span class="sxs-lookup"><span data-stu-id="9dc44-117">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="9dc44-118">Чтобы исправить такую ситуацию, используйте метод обратных вызовов, отмеченный <xref:System.Runtime.Serialization.OnDeserializingAttribute>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="9dc44-118">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="9dc44-119">Для каждого типа можно отметить только один метод каждым из предыдущих атрибутов обратных вызовов.</span><span class="sxs-lookup"><span data-stu-id="9dc44-119">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9dc44-120">Пример</span><span class="sxs-lookup"><span data-stu-id="9dc44-120">Example</span></span>  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="9dc44-121">См. также</span><span class="sxs-lookup"><span data-stu-id="9dc44-121">See also</span></span>

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [<span data-ttu-id="9dc44-122">Независимая от версий сериализация</span><span class="sxs-lookup"><span data-stu-id="9dc44-122">Version Tolerant Serialization</span></span>](../../../../docs/standard/serialization/version-tolerant-serialization.md)
