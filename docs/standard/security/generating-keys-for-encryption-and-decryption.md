---
title: Создание ключей для шифрования и расшифровки
description: Узнайте, как создавать симметричные и асимметричные ключи для шифрования и расшифровки в .NET и управлять ими.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET Framework], keys
- symmetric keys
- asymmetric keys [.NET Framework]
- cryptography [.NET Framework], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
ms.openlocfilehash: f8c3633d18e200037235502487d0d91d42083241
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661813"
---
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="88562-103">Создание ключей для шифрования и расшифровки</span><span class="sxs-lookup"><span data-stu-id="88562-103">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="88562-104">Создание ключей и управление ими — это важная часть процесса шифрования.</span><span class="sxs-lookup"><span data-stu-id="88562-104">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="88562-105">Симметричные алгоритмы требуют создания ключа и вектора инициализации (IV).</span><span class="sxs-lookup"><span data-stu-id="88562-105">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="88562-106">Ключ следует хранить в тайне от любого, кто не должен расшифровывать ваши данные.</span><span class="sxs-lookup"><span data-stu-id="88562-106">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="88562-107">Вектор инициализации может не быть секретным, но должен изменяться для каждого сеанса.</span><span class="sxs-lookup"><span data-stu-id="88562-107">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="88562-108">Асимметричные алгоритмы требуют создания открытого ключа и закрытого ключа.</span><span class="sxs-lookup"><span data-stu-id="88562-108">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="88562-109">Открытый ключ можно предоставлять кому угодно, а закрытый ключ должен быть известен только той стороне, которая будет расшифровывать данные, зашифрованные при помощи открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="88562-109">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="88562-110">В этом разделе описывается создание ключей и управление ими для симметричных и асимметричных алгоритмов.</span><span class="sxs-lookup"><span data-stu-id="88562-110">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="88562-111">симметричные ключи;</span><span class="sxs-lookup"><span data-stu-id="88562-111">Symmetric Keys</span></span>  
 <span data-ttu-id="88562-112">Классы симметричного шифрования, предоставляемые платформой .NET Framework, требуют ключ и новый вектор инициализации (IV) для шифрования и расшифровки данных.</span><span class="sxs-lookup"><span data-stu-id="88562-112">The symmetric encryption classes supplied by the .NET Framework require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="88562-113">При создании нового экземпляра одного из управляемых симметричных криптографических классов с помощью конструктора без параметров автоматически создаются новые ключ и вектор инициализации.</span><span class="sxs-lookup"><span data-stu-id="88562-113">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the parameterless constructor, a new key and IV are automatically created.</span></span> <span data-ttu-id="88562-114">Все пользователи, которым вы разрешаете расшифровывать свои данные, должны иметь тот же ключ и вектора инициализации и использовать тот же алгоритм.</span><span class="sxs-lookup"><span data-stu-id="88562-114">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="88562-115">Как правило, новый ключ и вектор инициализации должны создаваться для каждого сеанса, и ни вектор инициализации, ни ключ нельзя сохранять для использования в следующем сеансе.</span><span class="sxs-lookup"><span data-stu-id="88562-115">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="88562-116">При передаче симметричного ключа и вектора инициализации на удаленную сторону симметричный ключ обычно шифруется с помощью асимметричного шифрования.</span><span class="sxs-lookup"><span data-stu-id="88562-116">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="88562-117">Отправка ключа через незащищенную сеть без шифрования небезопасна, так как любой, кто перехватит ключ и вектор инициализации, сможет расшифровать данные.</span><span class="sxs-lookup"><span data-stu-id="88562-117">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span> <span data-ttu-id="88562-118">Дополнительные сведения об обмене данными с помощью шифрования см. в разделе [Создание криптографической схемы](creating-a-cryptographic-scheme.md).</span><span class="sxs-lookup"><span data-stu-id="88562-118">For more information about exchanging data by using encryption, see [Creating a Cryptographic Scheme](creating-a-cryptographic-scheme.md).</span></span>  
  
 <span data-ttu-id="88562-119">В следующем примере показано создание нового экземпляра класса <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> , реализующего алгоритм TripleDES.</span><span class="sxs-lookup"><span data-stu-id="88562-119">The following example shows the creation of a new instance of the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class that implements the TripleDES algorithm.</span></span>  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
```  
  
 <span data-ttu-id="88562-120">При выполнении предыдущего кода осуществляется создание нового ключа и вектора инициализации и их помещение в свойства **Key** и **IV** соответственно.</span><span class="sxs-lookup"><span data-stu-id="88562-120">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="88562-121">Иногда может понадобиться создать несколько ключей.</span><span class="sxs-lookup"><span data-stu-id="88562-121">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="88562-122">В этом случае можно создать новый экземпляр класса, реализующий симметричный алгоритм, а затем создать новый ключ и вектор инициализации, вызвав методы **GenerateKey** и **GenerateIV** .</span><span class="sxs-lookup"><span data-stu-id="88562-122">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="88562-123">В следующем примере кода показано, как создать новые ключи и IVs после внесения нового экземпляра симметричного криптографического класса.</span><span class="sxs-lookup"><span data-stu-id="88562-123">The following code example illustrates how to create new keys and IVs after a new instance of the symmetric cryptographic class has been made.</span></span>  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
tdes.GenerateIV()  
tdes.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
tdes.GenerateIV();  
tdes.GenerateKey();  
```  
  
 <span data-ttu-id="88562-124">При выполнении предыдущего кода ключ и вектор инициализации формируются, когда создается новый экземпляр **TripleDESCryptoServiceProvider** .</span><span class="sxs-lookup"><span data-stu-id="88562-124">When the previous code is executed, a key and IV are generated when the new instance of **TripleDESCryptoServiceProvider** is made.</span></span> <span data-ttu-id="88562-125">Другой ключ и вектор инициализации создаются при вызове методов **GenerateKey** и **GenerateIV** .</span><span class="sxs-lookup"><span data-stu-id="88562-125">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>  
  
## <a name="asymmetric-keys"></a><span data-ttu-id="88562-126">Асимметричные ключи</span><span class="sxs-lookup"><span data-stu-id="88562-126">Asymmetric Keys</span></span>  
 <span data-ttu-id="88562-127">Платформа .NET Framework предоставляет классы <xref:System.Security.Cryptography.RSACryptoServiceProvider> и <xref:System.Security.Cryptography.DSACryptoServiceProvider> для асимметричного шифрования.</span><span class="sxs-lookup"><span data-stu-id="88562-127">The .NET Framework provides the <xref:System.Security.Cryptography.RSACryptoServiceProvider> and <xref:System.Security.Cryptography.DSACryptoServiceProvider> classes for asymmetric encryption.</span></span> <span data-ttu-id="88562-128">Эти классы создают пару открытого и закрытого ключей при использовании конструктора без параметров для создания нового экземпляра.</span><span class="sxs-lookup"><span data-stu-id="88562-128">These classes create a public/private key pair when you use the parameterless constructor to create a new instance.</span></span> <span data-ttu-id="88562-129">Асимметричные ключи можно сохранять для использования в нескольких сеансах или создавать только для отдельного сеанса.</span><span class="sxs-lookup"><span data-stu-id="88562-129">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="88562-130">В то время как открытый ключ можно сделать общедоступным, закрытый ключ должен быть надежно защищен.</span><span class="sxs-lookup"><span data-stu-id="88562-130">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="88562-131">Пара из открытого и закрытого ключей создается каждый раз, когда создается новый экземпляр класса асимметричного алгоритма.</span><span class="sxs-lookup"><span data-stu-id="88562-131">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="88562-132">После создания нового экземпляра класса сведения ключа можно извлечь при помощи одного из двух методов:</span><span class="sxs-lookup"><span data-stu-id="88562-132">After a new instance of the class is created, the key information can be extracted using one of two methods:</span></span>  
  
- <span data-ttu-id="88562-133">метод <xref:System.Security.Cryptography.RSA.ToXmlString%2A> , возвращающий XML-представление сведений ключа;</span><span class="sxs-lookup"><span data-stu-id="88562-133">The <xref:System.Security.Cryptography.RSA.ToXmlString%2A> method, which returns an XML representation of the key information.</span></span>  
  
- <span data-ttu-id="88562-134">метод <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> , возвращающий структуру <xref:System.Security.Cryptography.RSAParameters> , которая содержит сведения ключа.</span><span class="sxs-lookup"><span data-stu-id="88562-134">The <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span>  
  
 <span data-ttu-id="88562-135">Оба метода принимают логическое значение, указывающее, следует ли возвращать только сведения об открытом ключе или сведения как об открытом, так и о закрытом ключе.</span><span class="sxs-lookup"><span data-stu-id="88562-135">Both methods accept a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span> <span data-ttu-id="88562-136">Класс **RSACryptoServiceProvider** можно инициализировать значением структуры **RSAParameters** при помощи метода <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> .</span><span class="sxs-lookup"><span data-stu-id="88562-136">An **RSACryptoServiceProvider** class can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> method.</span></span>  
  
 <span data-ttu-id="88562-137">Асимметричные закрытые ключи никогда не следует хранить буквальной форме или в формате обычного текста на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="88562-137">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="88562-138">Если необходимо хранить закрытый ключ, следует использовать для этого контейнер ключа.</span><span class="sxs-lookup"><span data-stu-id="88562-138">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="88562-139">Дополнительные сведения о хранении закрытого ключа в контейнере ключей см. в разделе [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="88562-139">For more on how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="88562-140">Следующий пример кода создает новый экземпляр класса **RSACryptoServiceProvider** посредством создания пары из открытого и закрытого ключей и сохраняет сведения об открытом ключе в структуре **RSAParameters** .</span><span class="sxs-lookup"><span data-stu-id="88562-140">The following code example creates a new instance of the **RSACryptoServiceProvider** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a><span data-ttu-id="88562-141">См. также</span><span class="sxs-lookup"><span data-stu-id="88562-141">See also</span></span>

- [<span data-ttu-id="88562-142">Шифрование данных</span><span class="sxs-lookup"><span data-stu-id="88562-142">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="88562-143">Расшифровка данных</span><span class="sxs-lookup"><span data-stu-id="88562-143">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="88562-144">Службы шифрования</span><span class="sxs-lookup"><span data-stu-id="88562-144">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="88562-145">Практическое руководство. Хранение асимметричных ключей в контейнере ключей</span><span class="sxs-lookup"><span data-stu-id="88562-145">How to: Store Asymmetric Keys in a Key Container</span></span>](how-to-store-asymmetric-keys-in-a-key-container.md)
