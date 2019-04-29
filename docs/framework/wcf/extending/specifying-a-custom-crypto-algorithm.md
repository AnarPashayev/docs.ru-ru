---
title: Задание пользовательского алгоритма шифрования
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: b365c3c8e74adcad03246a227d6593c49f8b3993
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768710"
---
# <a name="specifying-a-custom-crypto-algorithm"></a><span data-ttu-id="97ca2-102">Задание пользовательского алгоритма шифрования</span><span class="sxs-lookup"><span data-stu-id="97ca2-102">Specifying a Custom Crypto Algorithm</span></span>
<span data-ttu-id="97ca2-103">WCF позволяет указывать пользовательский алгоритм шифрования для использования при шифровании данных или вычислении цифровых подписей.</span><span class="sxs-lookup"><span data-stu-id="97ca2-103">WCF allows you to specify a custom crypto algorithm to use when encrypting data or computing digital signatures.</span></span> <span data-ttu-id="97ca2-104">Для этого выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="97ca2-104">This is done by the following steps:</span></span>  
  
1. <span data-ttu-id="97ca2-105">Создайте производный класс от класса <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="97ca2-105">Derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span></span>  
  
2. <span data-ttu-id="97ca2-106">Регистрация алгоритма</span><span class="sxs-lookup"><span data-stu-id="97ca2-106">Register the algorithm</span></span>  
  
3. <span data-ttu-id="97ca2-107">Настройте привязку с классом, который является производным от класса <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="97ca2-107">Configure the binding with the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class.</span></span>  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a><span data-ttu-id="97ca2-108">Создание производного класса от класса SecurityAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="97ca2-108">Derive a class from SecurityAlgorithmSuite</span></span>  
 <span data-ttu-id="97ca2-109"><xref:System.ServiceModel.Security.SecurityAlgorithmSuite> является абстрактным базовым классом, позволяющим указывать алгоритм, используемый при выполнении различных операций, связанных с безопасностью.</span><span class="sxs-lookup"><span data-stu-id="97ca2-109">The <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> is an abstract base class that allows you to specify the algorithm to use when performing various security related operations.</span></span> <span data-ttu-id="97ca2-110">Например, вычисление хэша для цифровой подписи или шифрование сообщения.</span><span class="sxs-lookup"><span data-stu-id="97ca2-110">For example, computing a hash for a digital signature or encrypting a message.</span></span> <span data-ttu-id="97ca2-111">В следующем коде показано, как наследовать класс от класса <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="97ca2-111">The following code shows how to derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span></span>  
  
```csharp  
public class MyCustomAlgorithmSuite : SecurityAlgorithmSuite  
    {  
        public override string DefaultAsymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaOaepKeyWrap; }  
        }  
  
        public override string DefaultAsymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaSha1Signature; }  
        }  
  
        public override string DefaultCanonicalizationAlgorithm  
        {  
            get { return SecurityAlgorithms.ExclusiveC14n; ; }  
        }  
  
        public override string DefaultDigestAlgorithm  
        {  
            get { return SecurityAlgorithms.MyCustomHashAlgorithm; }  
        }  
  
        public override string DefaultEncryptionAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override int DefaultEncryptionKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSignatureKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSymmetricKeyLength  
        {  
            get { return 128; }  
        }  
  
        public override string DefaultSymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override string DefaultSymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.HmacSha1Signature; }  
        }  
  
        public override bool IsAsymmetricKeyLengthSupported(int length)  
        {  
            return length >= 1024 && length <= 4096;  
        }  
  
        public override bool IsSymmetricKeyLengthSupported(int length)  
        {  
            return length >= 128 && length <= 256;  
        }  
    }  
```  
  
## <a name="register-the-custom-algorithm"></a><span data-ttu-id="97ca2-112">Регистрация пользовательского алгоритма</span><span class="sxs-lookup"><span data-stu-id="97ca2-112">Register the Custom Algorithm</span></span>  
 <span data-ttu-id="97ca2-113">Регистрацию можно выполнить в файле конфигурации или в императивном коде.</span><span class="sxs-lookup"><span data-stu-id="97ca2-113">Registration can be done in a configuration file or in imperative code.</span></span> <span data-ttu-id="97ca2-114">Регистрация пользовательского алгоритма выполняется путем создания сопоставления между классом, реализующим поставщик службы шифрования, и псевдонимом.</span><span class="sxs-lookup"><span data-stu-id="97ca2-114">Registering a custom algorithm is done by creating a mapping between a class that implements a crypto service provider and an alias.</span></span> <span data-ttu-id="97ca2-115">Затем псевдоним сопоставляется с URI, который используется при указании алгоритма в привязке службы WCF.</span><span class="sxs-lookup"><span data-stu-id="97ca2-115">The alias is then mapped to a URI which is used when specifying the algorithm in the WCF service’s binding.</span></span> <span data-ttu-id="97ca2-116">Следующий фрагмент конфигурации показывает, как зарегистрировать пользовательский алгоритм в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="97ca2-116">The following configuration snippet illustrates how to register a custom algorithm in config:</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://constoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="97ca2-117">В разделе <`cryptoClasses`> создает сопоставление между поставщиком SHA256CryptoServiceProvider и псевдонимом «SHA256CSP».</span><span class="sxs-lookup"><span data-stu-id="97ca2-117">The section under the <`cryptoClasses`> element creates the mapping between the SHA256CryptoServiceProvider and the alias "SHA256CSP".</span></span> <span data-ttu-id="97ca2-118"><`nameEntry`> Создает сопоставление между псевдонимом «SHA256CSP» и указанным URL-адрес (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).</span><span class="sxs-lookup"><span data-stu-id="97ca2-118">The <`nameEntry`> element creates the mapping between the "SHA256CSP" alias and the specified URL (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).</span></span>  
  
 <span data-ttu-id="97ca2-119">Для регистрации пользовательского алгоритма в коде используйте метод <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])>.</span><span class="sxs-lookup"><span data-stu-id="97ca2-119">To register the custom algorithm in code use the <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> method.</span></span> <span data-ttu-id="97ca2-120">Этот метод создает и оба сопоставления.</span><span class="sxs-lookup"><span data-stu-id="97ca2-120">This method creates both mappings.</span></span> <span data-ttu-id="97ca2-121">В следующем примере показано, как вызвать этот метод.</span><span class="sxs-lookup"><span data-stu-id="97ca2-121">The following example shows how to call this method:</span></span>  
  
```  
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a><span data-ttu-id="97ca2-122">Настройка привязки</span><span class="sxs-lookup"><span data-stu-id="97ca2-122">Configure the Binding</span></span>  
 <span data-ttu-id="97ca2-123">Привязка настраивается путем указания пользовательского класса, являющегося производным от класса <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, в параметрах привязки, как показано в следующем фрагменте кода.</span><span class="sxs-lookup"><span data-stu-id="97ca2-123">You configure the binding by specifying the custom <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class in the binding settings as shown in the following code snippet:</span></span>  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 <span data-ttu-id="97ca2-124">Полный пример кода, см. в разделе [криптографическая гибкость в системе безопасности WCF](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) образца.</span><span class="sxs-lookup"><span data-stu-id="97ca2-124">For a complete code example, see the [Cryptographic Agility in WCF Security](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97ca2-125">См. также</span><span class="sxs-lookup"><span data-stu-id="97ca2-125">See also</span></span>

- [<span data-ttu-id="97ca2-126">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="97ca2-126">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="97ca2-127">Защита служб</span><span class="sxs-lookup"><span data-stu-id="97ca2-127">Securing Services</span></span>](../../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="97ca2-128">Общие сведения о безопасности</span><span class="sxs-lookup"><span data-stu-id="97ca2-128">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="97ca2-129">Основные понятия безопасности</span><span class="sxs-lookup"><span data-stu-id="97ca2-129">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)
