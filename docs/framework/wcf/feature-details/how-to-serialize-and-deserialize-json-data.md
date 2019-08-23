---
title: Практическое руководство. Сериализация и десериализация данных JSON
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 0bebdbb3d74d58db093c4ec1e0e88138c7080335
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947894"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a>Практическое руководство. Сериализация и десериализация данных JSON
JSON - эффективный формат кодирования данных, обеспечивающий быстрый обмен небольшими объемами данных между клиентскими браузерами и веб-службами с поддержкой AJAX.  
  
 В этой статье показано, как сериализовать объекты типа .NET в данные в кодировке JSON, а затем десериализовать данные в формате JSON обратно в экземпляры типов .NET. В этом примере используется контракт данных для демонстрации сериализации и десериализации определяемого `Person` пользователем типа и использования. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>  
  
 Как правило, сериализация и десериализация JSON автоматически обрабатываются Windows Communication Foundation (WCF) при использовании типов контрактов данных в операциях службы, которые доступны через конечные точки с поддержкой AJAX. Однако в некоторых случаях может потребоваться непосредственная работа с данными JSON.   
  
> [!NOTE]
> Если ошибка возникает во время сериализации исходящего ответа на сервере или по какой-либо другой причине, она может не возвращаться клиенту в качестве ошибки.  
  
 Эта статья основана на примере [сериализации JSON](../samples/json-serialization.md) .  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a>Определение контракта данных для типа Person 
  
1. Определите контракт данных для типа `Person`, применив атрибут <xref:System.Runtime.Serialization.DataContractAttribute> к классу и атрибут <xref:System.Runtime.Serialization.DataMemberAttribute> к элементам, которые требуется сериализовать. Дополнительные сведения о контрактах данных см. в разделе [проектирование контрактов служб](../designing-service-contracts.md).  
  
    ```csharp  
    [DataContract]  
    internal class Person  
    {  
        [DataMember]  
        internal string name;  
  
        [DataMember]  
        internal int age;  
    }  
    ```  
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a>Сериализация экземпляра типа Person в формат JSON  
  
1. Создайте экземпляр типа `Person`.  
  
    ```csharp  
    var p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. Сериализует объект в поток памяти с <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>помощью. `Person`  
  
    ```csharp  
    var stream1 = new MemoryStream();  
    var ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. С помощью метода <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> запишите данные JSON в поток.  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4. Отобразите выходные данные JSON.  
  
    ```csharp  
    stream1.Position = 0;  
    var sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a>Десериализация экземпляра типа Person из формата JSON  
  
1. Десериализуйте данные в кодировке JSON в новый экземпляр типа `Person` с помощью метода <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> сериализатора <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```csharp  
    stream1.Position = 0;  
    var p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2. Отобразите результаты.  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a>Пример  
  
```csharp  
// Create a User object and serialize it to a JSON stream.  
public static string WriteFromObject()  
{  
    // Create User object.  
    var user = new User("Bob", 42);  
  
    // Create a stream to serialize the object to.  
    var ms = new MemoryStream();  
  
    // Serializer the User object to the stream.  
    var ser = new DataContractJsonSerializer(typeof(User));  
    ser.WriteObject(ms, user);  
    byte[] json = ms.ToArray();  
    ms.Close();  
    return Encoding.UTF8.GetString(json, 0, json.Length);  
}  
  
// Deserialize a JSON stream to a User object.  
public static User ReadToObject(string json)  
{  
    var deserializedUser = new User();  
    var ms = new MemoryStream(Encoding.UTF8.GetBytes(json));  
    var ser = new DataContractJsonSerializer(deserializedUser.GetType());  
    deserializedUser = ser.ReadObject(ms) as User;  
    ms.Close();  
    return deserializedUser;  
}  
```  
  
> [!NOTE]
> Сериализатор JSON выдает исключение при сериализации контрактов данных, имеющих несколько элементов с одинаковым именем, как показано в следующем примере кода.  
  
```csharp  
[DataContract]  
public class TestDuplicateDataBase  
{  
    [DataMember]  
    public int field1 = 123;  
}

[DataContract]  
public class TestDuplicateDataDerived : TestDuplicateDataBase  
{  
    [DataMember]  
    public new int field1 = 999;  
}  
```  
  
## <a name="see-also"></a>См. также

- [Изолированная сериализация JSON](stand-alone-json-serialization.md)
- [Поддержка JSON и других форматов обмена данными](support-for-json-and-other-data-transfer-formats.md)
