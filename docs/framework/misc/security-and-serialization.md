---
title: Безопасность и сериализация
description: Ознакомьтесь со сведениями о безопасности и сериализации. Используйте SecurityPermission с заданным флагом SerializationFormatter для просмотра или изменения данных экземпляра объекта.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, serialization
- serialization, security
- secure coding, serialization
- security [.NET Framework], serialization
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
ms.openlocfilehash: 393e334e8165f55812681848070929bdfb03a2a5
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855690"
---
# <a name="security-and-serialization"></a><span data-ttu-id="af4db-104">Безопасность и сериализация</span><span class="sxs-lookup"><span data-stu-id="af4db-104">Security and serialization</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="af4db-105">Поскольку сериализация может разрешить другому коду просматривать или изменять данные экземпляра объекта, которые могут быть недоступны другим способом, требуется специальное разрешение кода, выполняющего сериализацию: <xref:System.Security.Permissions.SecurityPermission> с указанным флагом <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> .</span><span class="sxs-lookup"><span data-stu-id="af4db-105">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="af4db-106">При политике безопасности по умолчанию такое разрешение не предоставляется коду, загруженному из Интернета или интрасети, и дается только коду на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="af4db-106">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="af4db-107">Как правило, сериализуются все поля экземпляра объекта; это означает, что данные представлены в сериализованных данных для экземпляра.</span><span class="sxs-lookup"><span data-stu-id="af4db-107">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="af4db-108">Код, который может интерпретировать формат, может определять значения данных, независимо от доступности члена.</span><span class="sxs-lookup"><span data-stu-id="af4db-108">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="af4db-109">Аналогично, десериализация извлекает данные из сериализованного представления и задает состояние объекта напрямую, снова независимо от правил специальных возможностей.</span><span class="sxs-lookup"><span data-stu-id="af4db-109">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="af4db-110">Объект, содержащий важные для обеспечения безопасности данные, следует по возможности делать несериализуемым.</span><span class="sxs-lookup"><span data-stu-id="af4db-110">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="af4db-111">Если он должен быть сериализуемым, попробуйте сделать специальные поля хранения конфиденциальных данных несериализуемыми.</span><span class="sxs-lookup"><span data-stu-id="af4db-111">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="af4db-112">Если эти поля нельзя сделать несериализуемыми, конфиденциальные данные будут доступны любому коду, имеющему разрешение на сериализацию.</span><span class="sxs-lookup"><span data-stu-id="af4db-112">If those fields cannot be made nonserializable, the sensitive data will be exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="af4db-113">Убедитесь, что вредоносный код не может получить это разрешение.</span><span class="sxs-lookup"><span data-stu-id="af4db-113">Make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="af4db-114">Интерфейс <xref:System.Runtime.Serialization.ISerializable> предназначен для использования только инфраструктурой сериализации.</span><span class="sxs-lookup"><span data-stu-id="af4db-114">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="af4db-115">Однако если он не защищен, то потенциально может раскрыть конфиденциальные сведения.</span><span class="sxs-lookup"><span data-stu-id="af4db-115">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="af4db-116">Если вы обеспечиваете настраиваемую сериализацию путем реализации **ISerializable**, убедитесь, что вы приняли следующие меры предосторожности.</span><span class="sxs-lookup"><span data-stu-id="af4db-116">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="af4db-117">Вы должны явно защитить метод <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> , либо требуя **SecurityPermission** с указанным разрешением **SerializationFormatter** , либо убедившись, что никакие конфиденциальные сведения не раскрываются в выходных данных метода.</span><span class="sxs-lookup"><span data-stu-id="af4db-117">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="af4db-118">Пример:</span><span class="sxs-lookup"><span data-stu-id="af4db-118">For example:</span></span>  
  
    ```vb  
    Public Overrides<SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Sub GetObjectData(info As SerializationInfo, context As StreamingContext)  
    End Sub  
    ```  
  
    ```csharp  
    [SecurityPermissionAttribute(SecurityAction.Demand,SerializationFormatter
    =true)]  
    public override void GetObjectData(SerializationInfo info,
    StreamingContext context)  
    {  
    }  
    ```  
  
- <span data-ttu-id="af4db-119">Специальный конструктор, используемый для сериализации, также должен выполнять тщательную проверку входных данных и должен быть либо защищенным, либо закрытым, чтобы предотвратить несанкционированное использование вредоносным кодом.</span><span class="sxs-lookup"><span data-stu-id="af4db-119">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="af4db-120">Следует обеспечить те же проверки безопасности и разрешения, необходимые для получения экземпляра подобного класса любыми другими методами, например путем явного создания класса или его неявного создания через какую-либо фабрику.</span><span class="sxs-lookup"><span data-stu-id="af4db-120">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af4db-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="af4db-121">See also</span></span>

- [<span data-ttu-id="af4db-122">Правила написания безопасного кода</span><span class="sxs-lookup"><span data-stu-id="af4db-122">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
