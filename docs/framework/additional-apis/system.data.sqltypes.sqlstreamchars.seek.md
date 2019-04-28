---
title: Метод SqlStreamChars.Seek (Int64, SeekOrigin) (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 6f802428a73f229e948099788ec21f07efbfab76
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705796"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a><span data-ttu-id="ac111-102">Метод SqlStreamChars.Seek (Int64, SeekOrigin)</span><span class="sxs-lookup"><span data-stu-id="ac111-102">SqlStreamChars.Seek(Int64, SeekOrigin) Method</span></span>

<span data-ttu-id="ac111-103">При переопределении в производном классе задает позицию в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="ac111-103">When overridden in a derived class, sets the position within the current stream.</span></span> <span data-ttu-id="ac111-104">Дружественные сборки, содержащей этот метод связан с SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="ac111-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="ac111-105">Он предназначен для использования с SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ac111-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="ac111-106">Для других баз данных используйте механизм размещения, предоставляемый этой базы данных.</span><span class="sxs-lookup"><span data-stu-id="ac111-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a><span data-ttu-id="ac111-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="ac111-107">Parameters</span></span>

`offset`\
<span data-ttu-id="ac111-108">Смещение в байтах относительно `origin`.</span><span class="sxs-lookup"><span data-stu-id="ac111-108">A byte offset relative to `origin`.</span></span>

`origin`\
<span data-ttu-id="ac111-109">Одно из значений перечисления, указывающее опорную точку для получения новой позиции.</span><span class="sxs-lookup"><span data-stu-id="ac111-109">One of the enumeration values that indicates the reference point from which to obtain the new position.</span></span>

## <a name="returns"></a><span data-ttu-id="ac111-110">Returns</span><span class="sxs-lookup"><span data-stu-id="ac111-110">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="ac111-111">Новая позиция в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="ac111-111">The new position within the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="ac111-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="ac111-112">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="ac111-113">`SqlStreamChars.Seek` Метод является закрытым и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="ac111-113">The `SqlStreamChars.Seek` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="ac111-114">Майкрософт не поддерживает использование этого поля в рабочем приложении ни при каких обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="ac111-114">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="ac111-115">Требования</span><span class="sxs-lookup"><span data-stu-id="ac111-115">Requirements</span></span>

<span data-ttu-id="ac111-116">**Пространство имен:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="ac111-116">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="ac111-117">**Сборка:** System.Data (в System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="ac111-117">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="ac111-118">**Версии платформы .NET framework:** Доступно с версии 2.0.</span><span class="sxs-lookup"><span data-stu-id="ac111-118">**.NET Framework versions:** Available since 2.0.</span></span>