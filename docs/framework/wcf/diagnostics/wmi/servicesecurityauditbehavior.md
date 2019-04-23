---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: 30679e1f67c6943bf674a6bbd8bf12be090765a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979138"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="4066d-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="4066d-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="4066d-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="4066d-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4066d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4066d-104">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4066d-105">Методы</span><span class="sxs-lookup"><span data-stu-id="4066d-105">Methods</span></span>  
 <span data-ttu-id="4066d-106">Класс ServiceSecurityAuditBehavior не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="4066d-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4066d-107">Свойства</span><span class="sxs-lookup"><span data-stu-id="4066d-107">Properties</span></span>  
 <span data-ttu-id="4066d-108">Класс ServiceSecurityAuditBehavior имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="4066d-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="4066d-109">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="4066d-109">AuditLogLocation</span></span>  
 <span data-ttu-id="4066d-110">Тип данных: string</span><span class="sxs-lookup"><span data-stu-id="4066d-110">Data type: string</span></span>  
  
 <span data-ttu-id="4066d-111">Тип доступа: Только чтение</span><span class="sxs-lookup"><span data-stu-id="4066d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4066d-112">Местоположение журнала аудита.</span><span class="sxs-lookup"><span data-stu-id="4066d-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="4066d-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="4066d-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="4066d-114">Тип данных: string</span><span class="sxs-lookup"><span data-stu-id="4066d-114">Data type: string</span></span>  
  
 <span data-ttu-id="4066d-115">Тип доступа: Только чтение</span><span class="sxs-lookup"><span data-stu-id="4066d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4066d-116">Тип уровня проверки подлинности сообщений, используемый для записи в журнал событий аудита.</span><span class="sxs-lookup"><span data-stu-id="4066d-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="4066d-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="4066d-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="4066d-118">Тип данных: string</span><span class="sxs-lookup"><span data-stu-id="4066d-118">Data type: string</span></span>  
  
 <span data-ttu-id="4066d-119">Тип доступа: Только чтение</span><span class="sxs-lookup"><span data-stu-id="4066d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4066d-120">Типы событий авторизации, записываемых в журнал аудита.</span><span class="sxs-lookup"><span data-stu-id="4066d-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="4066d-121">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="4066d-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="4066d-122">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="4066d-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="4066d-123">Тип доступа: Только чтение</span><span class="sxs-lookup"><span data-stu-id="4066d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4066d-124">Логическое значение, задающее поведение для подавления ошибок записи в журнал аудита.</span><span class="sxs-lookup"><span data-stu-id="4066d-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4066d-125">Требования</span><span class="sxs-lookup"><span data-stu-id="4066d-125">Requirements</span></span>  
  
|<span data-ttu-id="4066d-126">MOF</span><span class="sxs-lookup"><span data-stu-id="4066d-126">MOF</span></span>|<span data-ttu-id="4066d-127">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4066d-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4066d-128">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="4066d-128">Namespace</span></span>|<span data-ttu-id="4066d-129">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="4066d-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4066d-130">См. также</span><span class="sxs-lookup"><span data-stu-id="4066d-130">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
