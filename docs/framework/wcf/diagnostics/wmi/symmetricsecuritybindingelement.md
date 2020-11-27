---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: c618b5b41790b04a84b4c50fe47baa2c0cb05ab2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274105"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="2baed-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2baed-102">SymmetricSecurityBindingElement</span></span>

<span data-ttu-id="2baed-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2baed-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2baed-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2baed-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2baed-105">Методы</span><span class="sxs-lookup"><span data-stu-id="2baed-105">Methods</span></span>  

 <span data-ttu-id="2baed-106">Класс SymmetricSecurityBindingElement не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="2baed-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2baed-107">Свойства</span><span class="sxs-lookup"><span data-stu-id="2baed-107">Properties</span></span>  

 <span data-ttu-id="2baed-108">Класс SymmetricSecurityBindingElement имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="2baed-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="2baed-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="2baed-109">MessageProtectionOrder</span></span>  

 <span data-ttu-id="2baed-110">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="2baed-110">Data type: string</span></span>  
  
 <span data-ttu-id="2baed-111">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="2baed-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2baed-112">Порядок шифрования и подписывания сообщений для данной привязки.</span><span class="sxs-lookup"><span data-stu-id="2baed-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="2baed-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="2baed-113">RequireSignatureConfirmation</span></span>  

 <span data-ttu-id="2baed-114">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="2baed-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="2baed-115">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="2baed-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2baed-116">Указывает, требует ли привязка подтверждения подписи.</span><span class="sxs-lookup"><span data-stu-id="2baed-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2baed-117">Требования</span><span class="sxs-lookup"><span data-stu-id="2baed-117">Requirements</span></span>  
  
|<span data-ttu-id="2baed-118">MOF</span><span class="sxs-lookup"><span data-stu-id="2baed-118">MOF</span></span>|<span data-ttu-id="2baed-119">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2baed-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2baed-120">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="2baed-120">Namespace</span></span>|<span data-ttu-id="2baed-121">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="2baed-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2baed-122">См. также</span><span class="sxs-lookup"><span data-stu-id="2baed-122">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
