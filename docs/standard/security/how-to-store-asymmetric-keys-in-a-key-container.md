---
title: Практическое руководство. Хранение асимметричных ключей в контейнере ключей
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- storing asymmetric keys
- keys, asymmetric
- encryption keys
- keys, storing in key containers
- asymmetric keys [.NET Framework]
- encryption [.NET Framework], asymmetric keys
- decryption keys
ms.assetid: 0dbcbd8d-0dcf-40e9-9f0c-e3f162d35ccc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c6fada360eda46dc695ab732a2573b135d823f0a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326194"
---
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a>Практическое руководство. Хранение асимметричных ключей в контейнере ключей
Асимметричные закрытые ключи никогда не следует хранить буквальной форме или в формате обычного текста на локальном компьютере. Если необходимо хранить закрытый ключ, следует использовать для этого контейнер ключа. Дополнительные сведения о контейнерах ключей см. в разделе [Общие сведения о контейнерах ключей RSA уровня компьютера и пользователя](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a>Порядок создания асимметричного ключа и сохранения его в контейнере ключей  
  
1. Создайте новый экземпляр класса <xref:System.Security.Cryptography.CspParameters> и передайте имя, которое должно вызывать контейнер ключей, в <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> поля.  
  
2. Создать новый экземпляр класса, производного от <xref:System.Security.Cryptography.AsymmetricAlgorithm> класса (обычно **RSACryptoServiceProvider** или **DSACryptoServiceProvider**) и передайте ранее созданный  **CspParameters** объекта в его конструктор.  
  
### <a name="to-delete-the-key-from-a-key-container"></a>Порядок удаления ключа из контейнера ключей  
  
1. Создайте новый экземпляр класса **CspParameters** и передайте имя, которое должно вызывать контейнер ключей, в поле **CspParameters.KeyContainerName**.  
  
2. Создайте новый экземпляр класса, производного от класса **AsymmetricAlgorithm** (обычно это **RSACryptoServiceProvider** или **DSACryptoServiceProvider**) и передайте ранее созданный объект **CspParameters** в его конструктор.  
  
3. Установите для свойства **PersistKeyInCSP** класса, являющегося производным от **AsymmetricAlgorithm**, значение **false** (**False** в Visual Basic).  
  
4. Вызовите метод **Clear** класса, производного от **AsymmetricAlgorithm**. Этот метод освобождает все ресурсы класса и очищает контейнер ключей.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как создать асимметричный ключ, сохранить его в контейнере ключей, затем извлечь ключ и удалить его из контейнера.  
  
 Обратите внимание, что код в методах `GenKey_SaveInContainer` и `GetKeyFromContainer` совпадает.  Если указать имя контейнера ключей для объекта <xref:System.Security.Cryptography.CspParameters> и передать его в объект <xref:System.Security.Cryptography.AsymmetricAlgorithm>, когда свойство <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> или <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> имеет значение true, происходит следующее.  Если контейнер ключей с указанным именем не существует, он создается, а ключ сохраняется.  Если контейнер ключей с указанным именем существует, то ключ в этом контейнере автоматически загружается в текущий объект <xref:System.Security.Cryptography.AsymmetricAlgorithm>.  Таким образом, код в методе `GenKey_SaveInContainer` сохраняет ключ, так как он выполняется первым, а код в методе `GetKeyFromContainer` загружает ключ, так как он выполняется вторым.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
 _  
  
Public Class StoreKey  
  
    Public Shared Sub Main()  
        Try  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
        Catch e As CryptographicException  
            Console.WriteLine(e.Message)  
        End Try  
    End Sub  
  
    Public Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        ' name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key added to container:  {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub GetKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Delete the key entry in the container.  
        rsa.PersistKeyInCsp = False  
  
        ' Call Clear to release resources and delete the key from the container.  
        rsa.Clear()  
  
        Console.WriteLine("Key deleted.")  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
  
public class StoreKey  
  
{  
    public static void Main()  
    {  
        try  
        {  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
        }  
        catch(CryptographicException e)  
        {  
            Console.WriteLine(e.Message);  
        }  
  
    }  
  
    public static void GenKey_SaveInContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key added to container: \n  {0}", rsa.ToXmlString(true));  
    }  
  
    public static void GetKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : \n {0}", rsa.ToXmlString(true));  
    }  
  
    public static void DeleteKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Delete the key entry in the container.  
        rsa.PersistKeyInCsp = false;  
  
        // Call Clear to release resources and delete the key from the container.  
        rsa.Clear();  
  
        Console.WriteLine("Key deleted.");  
    }  
}  
```  
  
```Output  
Key added to container:  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key retrieved from container :  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key deleted.  
Key added to container:  
<RSAKeyValue> Key Information B</RSAKeyValue>  
Key deleted.  
```  
  
## <a name="see-also"></a>См. также

- [Создание ключей для шифрования и расшифровки](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [Шифрование данных](../../../docs/standard/security/encrypting-data.md)
- [Расшифровка данных](../../../docs/standard/security/decrypting-data.md)
- [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)
