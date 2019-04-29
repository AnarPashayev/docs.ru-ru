---
title: Практическое руководство. Расшифровка XML-элементов с помощью симметричных ключей
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Rijndael
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c569407bac247e60075834e67fde9327ce6bc4a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795139"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a>Практическое руководство. Расшифровка XML-элементов с помощью симметричных ключей
Классы можно использовать в пространстве имен <xref:System.Security.Cryptography.Xml> для шифрования элемента XML-документа.  Шифрование XML-данных позволяет хранить или передавать важные XML-данные, не беспокоясь о том, что они могут быть прочитаны.  Этот пример кода выполняет расшифровку XML-элемента при помощи алгоритма AES, также известного как Rijndael.  
  
 Сведения о способах шифрования XML-элемента с помощью этой процедуры см. в разделе [как: Шифрование XML-элементов с помощью симметричного ключа](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
 При использовании симметричного алгоритма, такого как AES, для шифрования XML-данных необходимо использовать один и тот же ключ как для шифрования, так и для расшифровки XML-данных.  В этом примере предполагается, что зашифрованные XML-данные были зашифрованы при помощи того же ключа и что стороны, выполняющие шифрование и расшифровку, согласуют между собой используемый алгоритм и ключ.  В этом примере ключ AES не сохраняется и не шифруется внутри зашифрованного XML-документа.  
  
 Этот пример подходит для ситуаций, где отдельному приложению требуется зашифровать данные на основе хранящегося в памяти сеансового ключа или на основе криптографически стойкого ключа, полученного из пароля.  В ситуациях, когда два приложения и более нуждаются в общем доступе к зашифрованным XML-данным, рекомендуется использовать схему шифрования, основанную на асимметричном алгоритме или сертификате X.509.  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a>Расшифровка XML-элемента при помощи симметричного ключа  
  
1. Шифрование XML-элемента с помощью ранее созданного ключа, используя методики, описанные в [как: Шифрование XML-элементов с помощью симметричного ключа](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
2. Найдите <`EncryptedData`> элемент (определенный стандартом шифрования XML) в <xref:System.Xml.XmlDocument> , содержащий зашифрованный XML-документ, а затем создайте <xref:System.Xml.XmlElement> объект для представления этого элемента.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3. Создайте объект <xref:System.Security.Cryptography.Xml.EncryptedData>, загрузив необработанные XML-данные из ранее созданного объекта <xref:System.Xml.XmlElement>.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4. Создайте новый объект <xref:System.Security.Cryptography.Xml.EncryptedXml> и используйте его для расшифровки XML-данных при помощи того же ключа, который использовался для шифрования.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5. Замените зашифрованный элемент на вновь расшифрованный элемент в формате открытого текста в XML-документе.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a>Пример  
 В этом примере предполагается, что файл с именем `"test.xml"` существует в том же каталоге, что и скомпилированная программа.  Кроме того, предполагается, что `"test.xml"` содержит элемент `"creditcard"`.  Можно поместить следующий XML-код в файл с именем `test.xml` и использовать его вместе с данным примером.  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
  
- Чтобы скомпилировать этот пример, необходимо включить ссылку на `System.Security.dll`.  
  
- Включите следующие пространства имен: <xref:System.Xml>, <xref:System.Security.Cryptography> и <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 Никогда не храните криптографический ключ в формате обычного текста и не передавайте этот ключ в таком формате между компьютерами.  
  
 После завершения работы с симметричным криптографическим ключом очистите его из памяти, установив для каждого байта нулевое значение или вызвав метод <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> управляемого класса шифрования.  
  
## <a name="see-also"></a>См. также

- <xref:System.Security.Cryptography.Xml>
- [Практическое руководство. Шифрование XML-элементов с помощью симметричного ключа](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)
