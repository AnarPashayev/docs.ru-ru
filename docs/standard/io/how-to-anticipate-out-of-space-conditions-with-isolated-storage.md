---
title: Практическое руководство. Предупреждение нехватки места при изолированном хранении
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data stores, quotas
- isolated storage, quotas
- quantity of isolated storage used
- limit on isolated storage used
- stores, quotas
- stores, out of space conditions
- data storage using isolated storage, quotas
- storing data using isolated storage, quotas
- space remaining in isolated storage
- data stores, out of space conditions
- storing data using isolated storage, out of space conditions
- quotas for isolated storage
- isolated storage, out of space conditions
- data storage using isolated storage, out of space conditions
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf5144cb1abd3a916d2b5afc361c8c96a221d47e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372299"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a><span data-ttu-id="a6683-102">Практическое руководство. Предупреждение нехватки места при изолированном хранении</span><span class="sxs-lookup"><span data-stu-id="a6683-102">How to: Anticipate Out-of-Space Conditions with Isolated Storage</span></span>

<span data-ttu-id="a6683-103">Код, использующий изолированное хранилище, ограничен [квотой](../../../docs/standard/io/isolated-storage.md#quotas) на максимальный размер секции данных, в которой существуют изолированные файлы и каталоги хранения.</span><span class="sxs-lookup"><span data-stu-id="a6683-103">Code that uses isolated storage is constrained by a [quota](../../../docs/standard/io/isolated-storage.md#quotas) that specifies the maximum size for the data compartment in which isolated storage files and directories exist.</span></span> <span data-ttu-id="a6683-104">Эта квота определяется политикой безопасности и настраивается администраторами.</span><span class="sxs-lookup"><span data-stu-id="a6683-104">The quota is defined by security policy and is configurable by administrators.</span></span> <span data-ttu-id="a6683-105">Если при попытке записи данных превышается максимальный размер, создается исключение <xref:System.IO.IsolatedStorage.IsolatedStorageException> и операция завершается ошибкой.</span><span class="sxs-lookup"><span data-stu-id="a6683-105">If the maximum allowed size is exceeded when you try to write data, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown and the operation fails.</span></span> <span data-ttu-id="a6683-106">Это помогает предотвратить атаки типа "отказ в обслуживании", которые могут привести к неспособности приложения обрабатывать запросы из-за переполнения хранилища данных.</span><span class="sxs-lookup"><span data-stu-id="a6683-106">This helps prevent malicious denial-of-service attacks that could cause the application to refuse requests because data storage is filled.</span></span>

<span data-ttu-id="a6683-107">Чтобы заранее определить, может ли попытка записи привести к сбою по этой причине, класс <xref:System.IO.IsolatedStorage.IsolatedStorage> предоставляет три свойства <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A> и <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>, доступных только для чтения.</span><span class="sxs-lookup"><span data-stu-id="a6683-107">To help you determine whether a given write attempt is likely to fail for this reason, the <xref:System.IO.IsolatedStorage.IsolatedStorage> class provides three read-only properties: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span></span> <span data-ttu-id="a6683-108">С их помощью вы можете оценить, будет ли превышен максимальный размер при записи в хранилище.</span><span class="sxs-lookup"><span data-stu-id="a6683-108">You can use these properties to determine whether writing to the store will cause the maximum allowed size of the store to be exceeded.</span></span> <span data-ttu-id="a6683-109">Имейте в виду, что к изолированному хранилищу можно обращаться параллельно. Это означает, что доступное пространство хранилища может измениться в период между проверкой свободного места и попыткой записи в хранилище.</span><span class="sxs-lookup"><span data-stu-id="a6683-109">Keep in mind that isolated storage can be accessed concurrently; therefore, when you compute the amount of remaining storage, the storage space could be consumed by the time you try to write to the store.</span></span> <span data-ttu-id="a6683-110">Но максимальный размер операции всегда полезен для того, чтобы выявить приближение к лимиту доступного пространства в хранилище.</span><span class="sxs-lookup"><span data-stu-id="a6683-110">However, you can use the maximum size of the store to help determine whether the upper limit on available storage is about to be reached.</span></span>

<span data-ttu-id="a6683-111">Правильность работы свойства <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> зависит от свидетельства из сборки.</span><span class="sxs-lookup"><span data-stu-id="a6683-111">The <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> property depends on evidence from the assembly to work properly.</span></span> <span data-ttu-id="a6683-112">Поэтому это свойство следует использовать только для объектов <xref:System.IO.IsolatedStorage.IsolatedStorageFile>, созданных с помощью методов <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> или <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>.</span><span class="sxs-lookup"><span data-stu-id="a6683-112">For this reason, you should retrieve this property only on <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="a6683-113">Объекты <xref:System.IO.IsolatedStorage.IsolatedStorageFile>, созданные другими способами (например, возвращаемые методом <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>), не возвращают точный максимальный размер.</span><span class="sxs-lookup"><span data-stu-id="a6683-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created in any other way (for example, objects that were returned from the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method) will not return an accurate maximum size.</span></span>

## <a name="example"></a><span data-ttu-id="a6683-114">Пример</span><span class="sxs-lookup"><span data-stu-id="a6683-114">Example</span></span>

<span data-ttu-id="a6683-115">Приведенный ниже пример кода получает изолированное хранилище, создает в нем несколько файлов и извлекает свойство <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>.</span><span class="sxs-lookup"><span data-stu-id="a6683-115">The following code example obtains an isolated store, creates a few files, and retrieves the <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> property.</span></span> <span data-ttu-id="a6683-116">Это свойство возвращает остаток свободного места в байтах.</span><span class="sxs-lookup"><span data-stu-id="a6683-116">The remaining space is reported in bytes.</span></span>

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a><span data-ttu-id="a6683-117">См. также</span><span class="sxs-lookup"><span data-stu-id="a6683-117">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="a6683-118">Изолированное хранилище</span><span class="sxs-lookup"><span data-stu-id="a6683-118">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
- [<span data-ttu-id="a6683-119">Практическое руководство. Получение хранилищ для изолированного хранения</span><span class="sxs-lookup"><span data-stu-id="a6683-119">How to: Obtain Stores for Isolated Storage</span></span>](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
