---
title: Практическое руководство. Создание пользовательского утверждения
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 399aba1a6ad70ae37355f529a291ab2f604af03f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797086"
---
# <a name="how-to-create-a-custom-claim"></a>Практическое руководство. Создание пользовательского утверждения
Инфраструктура модели удостоверений в Windows Communication Foundation (WCF) предоставляет набор встроенных типов утверждений и прав с вспомогательными функциями для создания <xref:System.IdentityModel.Claims.Claim> экземпляров с этими типами и правами. Эти встроенные утверждения предназначены для моделирования сведений, находящихся в типах учетных данных клиента, которые WCF поддерживает по умолчанию. Очень часто бывает достаточно встроенных утверждений; однако некоторые приложения требуют пользовательских утверждений. Утверждение состоит из типа утверждения, ресурса, к которому применяется утверждение, и права, подтверждающегося через этот ресурс. В этом разделе описывается создание пользовательского утверждения.  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>Создание пользовательского утверждения на основе примитивного типа данных  
  
1. Создайте пользовательское утверждение, передав тип утверждения, значение ресурса и право конструктору <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29>.  
  
    1. Выберите уникальное значение для типа утверждения.  
  
         Тип утверждения - это уникальный идентификатор строки. На конструктор пользовательского утверждения возлагается обязанность убедиться в уникальности идентификатора строки, используемого для данного типа утверждения. Список типов утверждений, определенных WCF, см. в <xref:System.IdentityModel.Claims.ClaimTypes> разделе класс.  
  
    2. Выберите примитивный тип данных и значение для ресурса.  
  
         Ресурс - это объект. Тип среды CLR ресурса может быть примитивом, например <xref:System.String> или <xref:System.Int32>, или любым сериализуемым типом. Тип CLR ресурса должен быть сериализуемым, поскольку утверждения сериализуются в различных точках WCF. Примитивные типы являются сериализуемыми.  
  
    3. Выберите право, определенное в WCF, или уникальное значение для настраиваемого права.  
  
         Право - это уникальный идентификатор строки. Права, определенные в WCF, определяются в <xref:System.IdentityModel.Claims.Rights> классе.  
  
         На конструктор пользовательского утверждения возлагается обязанность убедиться в уникальности идентификатора строки, используемого для данного права.  
  
         В следующем примере кода показано создание пользовательского утверждения с типом утверждения `http://example.org/claims/simplecustomclaim` для ресурса с именем `Driver's License` и правом <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>.  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>Создание пользовательского утверждения на основе непримитивного типа данных  
  
1. Создайте пользовательское утверждение, передав тип утверждения, значение ресурса и право конструктору <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29>.  
  
    1. Выберите уникальное значение для типа утверждения.  
  
         Тип утверждения - это уникальный идентификатор строки. На конструктор пользовательского утверждения возлагается обязанность убедиться в уникальности идентификатора строки, используемого для данного типа утверждения. Список типов утверждений, определенных WCF, см. в <xref:System.IdentityModel.Claims.ClaimTypes> разделе класс.  
  
    2. Выберите или определите сериализуемый непримитивный тип для ресурса.  
  
         Ресурс - это объект. Тип CLR ресурса должен быть сериализуемым, поскольку утверждения сериализуются в различных точках WCF. Примитивные типы уже являются сериализуемыми.  
  
         При определении нового типа примените к классу атрибут <xref:System.Runtime.Serialization.DataContractAttribute>. Также примените атрибут <xref:System.Runtime.Serialization.DataMemberAttribute> ко всем членам нового типа, которые необходимо сериализовать как часть утверждения.  
  
         В следующем примере кода определяется пользовательский тип ресурса с именем `MyResourceType`.  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3. Выберите право, определенное в WCF, или уникальное значение для настраиваемого права.  
  
         Право - это уникальный идентификатор строки. Права, определенные в WCF, определяются в <xref:System.IdentityModel.Claims.Rights> классе.  
  
         На конструктор пользовательского утверждения возлагается обязанность убедиться в уникальности идентификатора строки, используемого для данного права.  
  
         В следующем примере кода показано создание пользовательского утверждения с типом утверждения `http://example.org/claims/complexcustomclaim`, пользовательским типом ресурса `MyResourceType` и правом <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>.  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется создание пользовательского утверждения с примитивным типом ресурса и пользовательского утверждения с непримитивным типом ресурса.  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>См. также

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Управление утверждениями и авторизацией с помощью модели удостоверения](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
