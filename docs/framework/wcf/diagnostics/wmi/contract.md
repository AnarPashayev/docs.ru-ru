---
title: Контракт
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 0df39bbd0b273f1e898ccbe585be288cc245b7f5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274144"
---
# <a name="contract"></a><span data-ttu-id="89c29-102">Контракт</span><span class="sxs-lookup"><span data-stu-id="89c29-102">Contract</span></span>

<span data-ttu-id="89c29-103">Контракт</span><span class="sxs-lookup"><span data-stu-id="89c29-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89c29-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="89c29-104">Syntax</span></span>  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="89c29-105">Методы</span><span class="sxs-lookup"><span data-stu-id="89c29-105">Methods</span></span>  

 <span data-ttu-id="89c29-106">Класс контракта не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="89c29-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="89c29-107">Свойства</span><span class="sxs-lookup"><span data-stu-id="89c29-107">Properties</span></span>  

 <span data-ttu-id="89c29-108">Класс контракта имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="89c29-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="89c29-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="89c29-109">AppDomainId</span></span>  

 <span data-ttu-id="89c29-110">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="89c29-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="89c29-111">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="89c29-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="89c29-112">Идентификатор домена приложения, который размещает контракт.</span><span class="sxs-lookup"><span data-stu-id="89c29-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="89c29-113">Расширения функциональности</span><span class="sxs-lookup"><span data-stu-id="89c29-113">Behaviors</span></span>  

 <span data-ttu-id="89c29-114">Тип данных: массив Behavior</span><span class="sxs-lookup"><span data-stu-id="89c29-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="89c29-115">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="89c29-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="89c29-116">Поведения, связанные с этим контрактом.</span><span class="sxs-lookup"><span data-stu-id="89c29-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="89c29-117">name</span><span class="sxs-lookup"><span data-stu-id="89c29-117">Name</span></span>  

 <span data-ttu-id="89c29-118">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="89c29-118">Data type: string</span></span>  
  
 <span data-ttu-id="89c29-119">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="89c29-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="89c29-120">Имя контракта в WSDL.</span><span class="sxs-lookup"><span data-stu-id="89c29-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="89c29-121">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="89c29-121">Namespace</span></span>  

 <span data-ttu-id="89c29-122">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="89c29-122">Data type: string</span></span>  
  
 <span data-ttu-id="89c29-123">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="89c29-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="89c29-124">Пространство имен элемента `portType` в WSDL.</span><span class="sxs-lookup"><span data-stu-id="89c29-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="89c29-125">Операции</span><span class="sxs-lookup"><span data-stu-id="89c29-125">Operations</span></span>  

 <span data-ttu-id="89c29-126">Тип данных: массив Operation</span><span class="sxs-lookup"><span data-stu-id="89c29-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="89c29-127">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="89c29-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="89c29-128">Операции данного контракта.</span><span class="sxs-lookup"><span data-stu-id="89c29-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="89c29-129">ProcessId</span><span class="sxs-lookup"><span data-stu-id="89c29-129">ProcessId</span></span>  

 <span data-ttu-id="89c29-130">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="89c29-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="89c29-131">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="89c29-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="89c29-132">Идентификатор процесса, который размещает контракт.</span><span class="sxs-lookup"><span data-stu-id="89c29-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="89c29-133">ref</span><span class="sxs-lookup"><span data-stu-id="89c29-133">ref</span></span>  

 <span data-ttu-id="89c29-134">Тип данных: Contract</span><span class="sxs-lookup"><span data-stu-id="89c29-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="89c29-135">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="89c29-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="89c29-136">Тип обратного вызова, когда контракт является дуплексным.</span><span class="sxs-lookup"><span data-stu-id="89c29-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="89c29-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="89c29-137">SessionMode</span></span>  

 <span data-ttu-id="89c29-138">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="89c29-138">Data type: string</span></span>  
  
 <span data-ttu-id="89c29-139">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="89c29-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="89c29-140">Указывает, требуется ли для контракта, чтобы связанная с ним привязка использовала сеансы канала.</span><span class="sxs-lookup"><span data-stu-id="89c29-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="89c29-141">Тип</span><span class="sxs-lookup"><span data-stu-id="89c29-141">Type</span></span>  

 <span data-ttu-id="89c29-142">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="89c29-142">Data type: string</span></span>  
  
 <span data-ttu-id="89c29-143">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="89c29-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="89c29-144">Тип контракта.</span><span class="sxs-lookup"><span data-stu-id="89c29-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89c29-145">Требования</span><span class="sxs-lookup"><span data-stu-id="89c29-145">Requirements</span></span>  
  
|<span data-ttu-id="89c29-146">MOF</span><span class="sxs-lookup"><span data-stu-id="89c29-146">MOF</span></span>|<span data-ttu-id="89c29-147">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="89c29-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="89c29-148">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="89c29-148">Namespace</span></span>|<span data-ttu-id="89c29-149">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="89c29-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89c29-150">См. также</span><span class="sxs-lookup"><span data-stu-id="89c29-150">See also</span></span>

- <xref:System.ServiceModel.Description.ContractDescription>
