---
title: Строгое именование (справочник по управляемым API)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 7e431f3a41fadb7247f20d7ab9bb9120e827b0cd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732298"
---
# <a name="strong-naming-unmanaged-api-reference"></a><span data-ttu-id="36f13-102">Строгое именование (справочник по управляемым API)</span><span class="sxs-lookup"><span data-stu-id="36f13-102">Strong Naming (Unmanaged API Reference)</span></span>

<span data-ttu-id="36f13-103">API строгого именования позволяет клиенту администрировать подписание сборок строгим именем.</span><span class="sxs-lookup"><span data-stu-id="36f13-103">The strong naming API enables a client to administer strong name signing for assemblies.</span></span>  
  
 <span data-ttu-id="36f13-104">При подписи сборки строгим именем в файл, содержащий манифест сборки, добавляется зашифрованный открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="36f13-104">Signing an assembly with a strong name adds a public key encryption to the file containing the assembly manifest.</span></span> <span data-ttu-id="36f13-105">Подпись строгим именем гарантирует уникальность имени, предотвращает подмену имени и после разрешения ссылки предоставляет уникальный идентификатор вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="36f13-105">Strong name signing helps verify name uniqueness, prevents name spoofing, and provides callers with a unique identity when a reference is resolved.</span></span> <span data-ttu-id="36f13-106">Однако со строгим именем не связано никакого уровня доверия.</span><span class="sxs-lookup"><span data-stu-id="36f13-106">However, no level of trust is associated with a strong name.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="36f13-107">в этом разделе</span><span class="sxs-lookup"><span data-stu-id="36f13-107">In This Section</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36f13-108">Все эти функции являются нерекомендуемыми начиная с .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-108">All of these functions have been deprecated starting with the .NET Framework 4.</span></span> <span data-ttu-id="36f13-109">Рекомендуемые альтернативы см. в интерфейсе [ICLRStrongName](../hosting/iclrstrongname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="36f13-109">For suggested alternatives, see the [ICLRStrongName](../hosting/iclrstrongname-interface.md) interface.</span></span>  
  
 [<span data-ttu-id="36f13-110">Функция GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="36f13-110">GetHashFromAssemblyFile Function</span></span>](gethashfromassemblyfile-function.md)  
 <span data-ttu-id="36f13-111">Получает хэш указанного файла сборки с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="36f13-111">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="36f13-112">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-112">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-113">Функция GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="36f13-113">GetHashFromAssemblyFileW Function</span></span>](gethashfromassemblyfilew-function.md)  
 <span data-ttu-id="36f13-114">Получает хэш файла сборки, указанного строкой Юникода, с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="36f13-114">Gets a hash of the assembly file specified as a Unicode string, using the specified hash algorithm.</span></span> <span data-ttu-id="36f13-115">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-115">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-116">Функция GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="36f13-116">GetHashFromBlob Function</span></span>](gethashfromblob-function.md)  
 <span data-ttu-id="36f13-117">Получает хэш сборки по указанному адресу памяти с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="36f13-117">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span> <span data-ttu-id="36f13-118">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-118">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-119">Функция GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="36f13-119">GetHashFromFile Function</span></span>](gethashfromfile-function.md)  
 <span data-ttu-id="36f13-120">Создает хэш содержимого указанного файла.</span><span class="sxs-lookup"><span data-stu-id="36f13-120">Generates a hash over the contents of the specified file.</span></span>  <span data-ttu-id="36f13-121">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-121">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-122">Функция GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="36f13-122">GetHashFromFileW Function</span></span>](gethashfromfilew-function.md)  
 <span data-ttu-id="36f13-123">Создает хэш содержимого файла, указанного строкой Юникода.</span><span class="sxs-lookup"><span data-stu-id="36f13-123">Generates a hash over the contents of the file specified by a Unicode string.</span></span> <span data-ttu-id="36f13-124">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-124">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-125">Функция GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="36f13-125">GetHashFromHandle Function</span></span>](gethashfromhandle-function.md)  
 <span data-ttu-id="36f13-126">Создает хэш содержимого файла с заданным дескриптором файла с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="36f13-126">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  <span data-ttu-id="36f13-127">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-127">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-128">Функция StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="36f13-128">StrongNameCompareAssemblies Function</span></span>](strongnamecompareassemblies-function.md)  
 <span data-ttu-id="36f13-129">Определяет, отличаются ли две сборки только подписями строгого имени.</span><span class="sxs-lookup"><span data-stu-id="36f13-129">Determines whether two assemblies differ only by their strong name signatures.</span></span> <span data-ttu-id="36f13-130">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-130">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-131">Функция StrongNameErrorInfo</span><span class="sxs-lookup"><span data-stu-id="36f13-131">StrongNameErrorInfo Function</span></span>](strongnameerrorinfo-function.md)  
 <span data-ttu-id="36f13-132">Получает код последней ошибки, вызванной одной из функций строгого имени.</span><span class="sxs-lookup"><span data-stu-id="36f13-132">Gets the last error code that was raised by one of the strong name functions.</span></span>  
  
 [<span data-ttu-id="36f13-133">Функция StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="36f13-133">StrongNameFreeBuffer Function</span></span>](strongnamefreebuffer-function.md)  
 <span data-ttu-id="36f13-134">Освобождает память, выделенную предыдущим вызовом функции строгого имени, такой как [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md) или [StrongNameSignatureGeneration ](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="36f13-134">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>   <span data-ttu-id="36f13-135">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-135">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-136">Функция StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="36f13-136">StrongNameGetBlob Function</span></span>](strongnamegetblob-function.md)  
 <span data-ttu-id="36f13-137">Заполняет указанный буфер двоичным представлением исполняемого файла по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="36f13-137">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span> <span data-ttu-id="36f13-138">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-138">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-139">Функция StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="36f13-139">StrongNameGetBlobFromImage Function</span></span>](strongnamegetblobfromimage-function.md)  
 <span data-ttu-id="36f13-140">Получает двоичное представление образа сборки по указанному адресу памяти.</span><span class="sxs-lookup"><span data-stu-id="36f13-140">Gets a binary representation of the assembly image at the specified memory address.</span></span> <span data-ttu-id="36f13-141">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-141">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-142">Функция StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="36f13-142">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)  
 <span data-ttu-id="36f13-143">Получает открытый ключ из пары закрытого и открытого ключей.</span><span class="sxs-lookup"><span data-stu-id="36f13-143">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="36f13-144">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-144">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-145">Функция StrongNameHashSize</span><span class="sxs-lookup"><span data-stu-id="36f13-145">StrongNameHashSize Function</span></span>](strongnamehashsize-function.md)  
 <span data-ttu-id="36f13-146">Получает размер буфера, необходимый для хэша, с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="36f13-146">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  <span data-ttu-id="36f13-147">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-147">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-148">Функция StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="36f13-148">StrongNameKeyDelete Function</span></span>](strongnamekeydelete-function.md)  
 <span data-ttu-id="36f13-149">Удаляет указанный контейнер ключей.</span><span class="sxs-lookup"><span data-stu-id="36f13-149">Deletes the specified key container.</span></span> <span data-ttu-id="36f13-150">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-150">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-151">Функция StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="36f13-151">StrongNameKeyGen Function</span></span>](strongnamekeygen-function.md)  
 <span data-ttu-id="36f13-152">Создает пару открытого и закрытого ключей для использования строгого имени.</span><span class="sxs-lookup"><span data-stu-id="36f13-152">Creates a new public/private key pair for strong name use.</span></span>  <span data-ttu-id="36f13-153">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-153">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-154">Функция StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="36f13-154">StrongNameKeyGenEx Function</span></span>](strongnamekeygenex-function.md)  
 <span data-ttu-id="36f13-155">Создает пару открытого и закрытого ключей с заданным размером для использования строгого имени.</span><span class="sxs-lookup"><span data-stu-id="36f13-155">Generates a new public/private key pair with the specified key size for strong name use.</span></span> <span data-ttu-id="36f13-156">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-156">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-157">Функция StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="36f13-157">StrongNameKeyInstall Function</span></span>](strongnamekeyinstall-function.md)  
 <span data-ttu-id="36f13-158">Импортирует пару открытого и закрытого ключей в контейнер.</span><span class="sxs-lookup"><span data-stu-id="36f13-158">Imports a public/private key pair into a container.</span></span>  <span data-ttu-id="36f13-159">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-159">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-160">Функция StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="36f13-160">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)  
 <span data-ttu-id="36f13-161">Создает подпись строгого имени для указанной сборки.</span><span class="sxs-lookup"><span data-stu-id="36f13-161">Generates a strong name signature for the specified assembly.</span></span>   <span data-ttu-id="36f13-162">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-162">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-163">Функция StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="36f13-163">StrongNameSignatureGenerationEx Function</span></span>](strongnamesignaturegenerationex-function.md)  
 <span data-ttu-id="36f13-164">Создает подпись строгого имени для указанной сборки в зависимости от указанных флагов.</span><span class="sxs-lookup"><span data-stu-id="36f13-164">Generates a strong name signature for the specified assembly, based on the specified flags.</span></span>    <span data-ttu-id="36f13-165">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-165">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-166">Функция StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="36f13-166">StrongNameSignatureSize Function</span></span>](strongnamesignaturesize-function.md)  
 <span data-ttu-id="36f13-167">Возвращает размер подписи строгого имени.</span><span class="sxs-lookup"><span data-stu-id="36f13-167">Returns the size of the strong name signature.</span></span> <span data-ttu-id="36f13-168">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-168">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-169">Функция StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="36f13-169">StrongNameSignatureVerification Function</span></span>](strongnamesignatureverification-function.md)  
 <span data-ttu-id="36f13-170">Получает значение, указывающее, содержит ли находящийся по указанному пути манифест сборки подпись строгого имени, которая проверяется в соответствии с заданными флагами.</span><span class="sxs-lookup"><span data-stu-id="36f13-170">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span> <span data-ttu-id="36f13-171">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-171">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-172">Функция StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="36f13-172">StrongNameSignatureVerificationEx Function</span></span>](strongnamesignatureverificationex-function.md)  
 <span data-ttu-id="36f13-173">Получает значение, указывающее, содержит ли находящийся по указанному пути манифест сборки подпись строгого имени.</span><span class="sxs-lookup"><span data-stu-id="36f13-173">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  <span data-ttu-id="36f13-174">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-174">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-175">Функция StrongNameSignatureVerificationFromImage</span><span class="sxs-lookup"><span data-stu-id="36f13-175">StrongNameSignatureVerificationFromImage Function</span></span>](strongnamesignatureverificationfromimage-function.md)  
 <span data-ttu-id="36f13-176">Проверяет допустимость сборки, которая уже была сопоставлена с памятью, для связанного открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="36f13-176">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span> <span data-ttu-id="36f13-177">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-177">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-178">Функция StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="36f13-178">StrongNameTokenFromAssembly Function</span></span>](strongnametokenfromassembly-function.md)  
 <span data-ttu-id="36f13-179">Создает маркер строгого имени из указанного файла сборки.</span><span class="sxs-lookup"><span data-stu-id="36f13-179">Creates a strong name token from the specified assembly file.</span></span>  <span data-ttu-id="36f13-180">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-180">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-181">Функция StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="36f13-181">StrongNameTokenFromAssemblyEx Function</span></span>](strongnametokenfromassemblyex-function.md)  
 <span data-ttu-id="36f13-182">Создает маркер строгого имени из указанного файла сборки и возвращает открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="36f13-182">Creates a strong name token from the specified assembly file, and returns the public key.</span></span> <span data-ttu-id="36f13-183">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-183">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-184">Функция StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="36f13-184">StrongNameTokenFromPublicKey Function</span></span>](strongnametokenfrompublickey-function.md)  
 <span data-ttu-id="36f13-185">Получает маркер, представляющий открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="36f13-185">Gets a token representing a public key.</span></span> <span data-ttu-id="36f13-186">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="36f13-186">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="36f13-187">Структура PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="36f13-187">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)  
 <span data-ttu-id="36f13-188">Представляет открытый ключ из пары открытого и закрытого ключей в двоичном формате.</span><span class="sxs-lookup"><span data-stu-id="36f13-188">Represents the public key of a public/private key pair in binary format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36f13-189">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="36f13-189">See also</span></span>

- [<span data-ttu-id="36f13-190">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="36f13-190">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="36f13-191">Справочник по неуправляемым API</span><span class="sxs-lookup"><span data-stu-id="36f13-191">Unmanaged API Reference</span></span>](../index.md)
