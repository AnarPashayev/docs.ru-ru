---
title: Практическое руководство. Использование защиты данных
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET Framework], data protection API
- data [.NET Framework], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET Framework], data protection API
- data protection API [.NET Framework]
- decryption
- data [.NET Framework], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2559ae686820b1972e457b013565aeb28842392e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933852"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="8ac10-102">Практическое руководство. Использование защиты данных</span><span class="sxs-lookup"><span data-stu-id="8ac10-102">How to: Use Data Protection</span></span>
<span data-ttu-id="8ac10-103">Платформа .NET Framework предоставляет доступ к API защиты данных (DPAPI), который позволяет шифровать данные, используя сведения из текущей учетной записи пользователя или с текущего компьютера.</span><span class="sxs-lookup"><span data-stu-id="8ac10-103">The .NET Framework provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="8ac10-104">Использование API защиты данных позволяет упростить сложную задачу явного создания и хранения криптографического ключа.</span><span class="sxs-lookup"><span data-stu-id="8ac10-104">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
 <span data-ttu-id="8ac10-105">Используйте класс <xref:System.Security.Cryptography.ProtectedMemory> для шифрования массива байтов в памяти.</span><span class="sxs-lookup"><span data-stu-id="8ac10-105">Use the <xref:System.Security.Cryptography.ProtectedMemory> class to encrypt an array of in-memory bytes.</span></span>  <span data-ttu-id="8ac10-106">Эта функциональность доступна в операционных системах Microsoft Windows XP и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="8ac10-106">This functionality is available in Microsoft Windows XP and later operating systems.</span></span>  <span data-ttu-id="8ac10-107">Можно указать, что память, зашифрованная текущим процессом, может быть расшифрована только текущим процессом, всеми процессами либо из того же контекста пользователя.</span><span class="sxs-lookup"><span data-stu-id="8ac10-107">You can specify that memory encrypted by the current process can be decrypted by the current process only, by all processes, or from the same user context.</span></span>  <span data-ttu-id="8ac10-108">Подробное описание параметров <xref:System.Security.Cryptography.ProtectedMemory> см. в разделе, посвященном перечислению <xref:System.Security.Cryptography.MemoryProtectionScope>.</span><span class="sxs-lookup"><span data-stu-id="8ac10-108">See the <xref:System.Security.Cryptography.MemoryProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedMemory> options.</span></span>  
  
 <span data-ttu-id="8ac10-109">Используйте класс <xref:System.Security.Cryptography.ProtectedData> для шифрования копии массива байтов.</span><span class="sxs-lookup"><span data-stu-id="8ac10-109">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="8ac10-110">Эта функциональность доступна в операционных системах Microsoft Windows 2000 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="8ac10-110">This functionality is available in Microsoft Windows 2000 and later operating systems.</span></span>  <span data-ttu-id="8ac10-111">Можно указать, что данные, зашифрованные текущей учетной записью пользователя, могут быть расшифрованы только той же учетной записью, либо можно указать, что данные, зашифрованные текущей учетной записью пользователя, могут быть расшифрованы любой учетной записью на компьютере.</span><span class="sxs-lookup"><span data-stu-id="8ac10-111">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="8ac10-112">Подробное описание параметров <xref:System.Security.Cryptography.ProtectedData> см. в разделе, посвященном перечислению <xref:System.Security.Cryptography.DataProtectionScope>.</span><span class="sxs-lookup"><span data-stu-id="8ac10-112">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="8ac10-113">Шифрование данных в памяти при помощи функции защиты данных</span><span class="sxs-lookup"><span data-stu-id="8ac10-113">To encrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="8ac10-114">Вызовите статический метод <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> во время передачи массива байтов для шифрования, энтропии и области защиты памяти.</span><span class="sxs-lookup"><span data-stu-id="8ac10-114">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the memory protection scope.</span></span>  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="8ac10-115">Расшифровка данных в памяти при помощи функции защиты данных</span><span class="sxs-lookup"><span data-stu-id="8ac10-115">To decrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="8ac10-116">Вызовите статический метод <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> во время передачи массива байтов для расшифровки и области защиты памяти.</span><span class="sxs-lookup"><span data-stu-id="8ac10-116">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> method while passing an array of bytes to decrypt and the memory protection scope.</span></span>  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="8ac10-117">Шифрование данных в файл или поток при помощи функции защиты данных</span><span class="sxs-lookup"><span data-stu-id="8ac10-117">To encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="8ac10-118">Создайте случайную энтропию.</span><span class="sxs-lookup"><span data-stu-id="8ac10-118">Create random entropy.</span></span>  
  
2. <span data-ttu-id="8ac10-119">Вызовите статический метод <xref:System.Security.Cryptography.ProtectedData.Protect%2A> во время передачи массива байтов для шифрования, энтропии и области защиты данных.</span><span class="sxs-lookup"><span data-stu-id="8ac10-119">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="8ac10-120">Запишите зашифрованные данные в файл или поток.</span><span class="sxs-lookup"><span data-stu-id="8ac10-120">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="8ac10-121">Расшифровка данных из файла или потока при помощи функции защиты данных</span><span class="sxs-lookup"><span data-stu-id="8ac10-121">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="8ac10-122">Считайте зашифрованные данные из файла или потока.</span><span class="sxs-lookup"><span data-stu-id="8ac10-122">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="8ac10-123">Вызовите статический метод <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> во время передачи массива байтов для расшифровки и области защиты данных.</span><span class="sxs-lookup"><span data-stu-id="8ac10-123">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ac10-124">Пример</span><span class="sxs-lookup"><span data-stu-id="8ac10-124">Example</span></span>  
 <span data-ttu-id="8ac10-125">В следующем примере кода показаны два вида шифрования и расшифровки.</span><span class="sxs-lookup"><span data-stu-id="8ac10-125">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="8ac10-126">Сначала пример кода выполняет шифрование и расшифровку массива байтов в памяти.</span><span class="sxs-lookup"><span data-stu-id="8ac10-126">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="8ac10-127">Далее этот пример кода шифрует копию массива байтов, сохраняет его в файл, загружает данные обратно из файла и затем расшифровывает эти данные.</span><span class="sxs-lookup"><span data-stu-id="8ac10-127">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="8ac10-128">В примере отображаются исходные данные, зашифрованные данные и расшифрованные данные.</span><span class="sxs-lookup"><span data-stu-id="8ac10-128">The example displays the original data, the encrypted data, and the decrypted data.</span></span>  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8ac10-129">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="8ac10-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="8ac10-130">Включите ссылку на `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="8ac10-130">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="8ac10-131">Включите пространство имен <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography> и <xref:System.Text>.</span><span class="sxs-lookup"><span data-stu-id="8ac10-131">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac10-132">См. также</span><span class="sxs-lookup"><span data-stu-id="8ac10-132">See also</span></span>

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
