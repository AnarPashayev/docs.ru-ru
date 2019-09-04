---
title: Спецификация манифеста поставщика
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 6b924f484e6635760d08d0eba9fb9436bdd8bc88
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248591"
---
# <a name="provider-manifest-specification"></a><span data-ttu-id="40866-102">Спецификация манифеста поставщика</span><span class="sxs-lookup"><span data-stu-id="40866-102">Provider Manifest Specification</span></span>
<span data-ttu-id="40866-103">В этом разделе описывается поддержка типов и функций в хранилище данных, представляемая поставщиком хранилища данных.</span><span class="sxs-lookup"><span data-stu-id="40866-103">This section discusses how a data store provider can support the types and functions in the data store.</span></span>  
  
 <span data-ttu-id="40866-104">Службы сущностей работают независимо от поставщика хранилища данных, однако позволяют поставщику явно определять порядок взаимодействия моделей, сопоставлений и запросов с базовым хранилищем данных.</span><span class="sxs-lookup"><span data-stu-id="40866-104">Entity Services operates independently of a specific data store provider yet still allows a data provider to explicitly define how models, mappings, and queries interact with an underlying data store.</span></span> <span data-ttu-id="40866-105">Без реализованного уровня абстракции службы сущностей могли бы работать только с поставщиком данных или хранилищем данных определенного типа.</span><span class="sxs-lookup"><span data-stu-id="40866-105">Without a layer of abstraction, Entity Services could only be targeted at a specific data store or data provider.</span></span>  
  
 <span data-ttu-id="40866-106">Типы, поддерживаемые поставщиком, явно или неявно поддерживаются базовой базой данных.</span><span class="sxs-lookup"><span data-stu-id="40866-106">Types that the provider supports are directly or indirectly supported by the underlying database.</span></span> <span data-ttu-id="40866-107">Эти типы необязательно совпадают с типами хранилища, но используются поставщиком для поддержки [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40866-107">These types are not necessarily the exact store types, but the types the provider uses to support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="40866-108">Типы поставщика и хранилища описываются в терминах модели EDM.</span><span class="sxs-lookup"><span data-stu-id="40866-108">Provider/store types are described in the Entity Data Model (EDM) terms.</span></span>  
  
 <span data-ttu-id="40866-109">Типы параметров и возвращаемых значений для функций, поддерживаемые хранилищем данных, выражаются в терминах модели EDM.</span><span class="sxs-lookup"><span data-stu-id="40866-109">Parameter and return types for the functions supported by the data store are specified in EDM terms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40866-110">Требования</span><span class="sxs-lookup"><span data-stu-id="40866-110">Requirements</span></span>  
 <span data-ttu-id="40866-111">Платформа [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] и хранилище данных должны иметь возможность обмениваться данными известных типов, исключая потерю и усечение данных.</span><span class="sxs-lookup"><span data-stu-id="40866-111">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and the data store need to be able to pass data back and forth in known types without any data loss or truncation.</span></span>  
  
 <span data-ttu-id="40866-112">Манифест поставщика должен загружаться средствами во время разработки без необходимости установления соединения с хранилищем данных.</span><span class="sxs-lookup"><span data-stu-id="40866-112">The provider manifest must be loadable by tools at design time without having to open a connection to the data store.</span></span>  
  
 <span data-ttu-id="40866-113">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Учитывается регистр, но базовое хранилище данных может быть недоступно.</span><span class="sxs-lookup"><span data-stu-id="40866-113">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is case sensitive, but the underlying data store may not be.</span></span> <span data-ttu-id="40866-114">Если артефакты EDM (например, идентификаторы и имена типов) определяются и используются в манифесте, в них необходимо учитывать регистр символов согласно требованиям [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40866-114">When EDM artifacts (identifiers and type names, for example) are defined and used in the manifest, they must use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] case sensitivity.</span></span> <span data-ttu-id="40866-115">Если в манифесте поставщика встречаются элементы хранилища данных, в которых может учитываться регистр, то в манифесте поставщика необходимо сохранять регистр.</span><span class="sxs-lookup"><span data-stu-id="40866-115">If data store elements that may be case sensitive appear in the provider manifest, that casing needs to be maintained in the provider manifest.</span></span>  
  
 <span data-ttu-id="40866-116">В [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] требуется манифест для всех поставщиков данных.</span><span class="sxs-lookup"><span data-stu-id="40866-116">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] requires a provider manifest for all data providers.</span></span> <span data-ttu-id="40866-117">При попытке использования поставщика, не имеющего манифеста поставщика с [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], возникнет ошибка.</span><span class="sxs-lookup"><span data-stu-id="40866-117">If you try to use a provider that does not have a provider manifest with the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you will get an error.</span></span>  
  
 <span data-ttu-id="40866-118">В следующей таблице описываются виды исключений, вызываемые [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], когда при взаимодействии с поставщиком создаются исключения.</span><span class="sxs-lookup"><span data-stu-id="40866-118">The following table describes the kinds of exceptions the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] would throw when exceptions arise through provider interaction:</span></span>  
  
|<span data-ttu-id="40866-119">Проблемы</span><span class="sxs-lookup"><span data-stu-id="40866-119">Issue</span></span>|<span data-ttu-id="40866-120">Исключение</span><span class="sxs-lookup"><span data-stu-id="40866-120">Exception</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="40866-121">Поставщик не поддерживает GetProviderManifest в DbProviderServices.</span><span class="sxs-lookup"><span data-stu-id="40866-121">The Provider does not support GetProviderManifest in DbProviderServices.</span></span>|<span data-ttu-id="40866-122">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="40866-122">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="40866-123">Отсутствует манифест поставщика: поставщик возвращает значение `null` при попытке получить манифест поставщика.</span><span class="sxs-lookup"><span data-stu-id="40866-123">Missing provider manifest: the provider returns `null` when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="40866-124">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="40866-124">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="40866-125">Недопустимый манифест поставщика: поставщик возвращает недопустимый XML-код при попытке получить манифест поставщика.</span><span class="sxs-lookup"><span data-stu-id="40866-125">Invalid provider manifest: the provider returns invalid XML when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="40866-126">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="40866-126">ProviderIncompatibleException</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="40866-127">Сценарии</span><span class="sxs-lookup"><span data-stu-id="40866-127">Scenarios</span></span>  
 <span data-ttu-id="40866-128">Поставщик должен поддерживать следующие сценарии:</span><span class="sxs-lookup"><span data-stu-id="40866-128">A provider should support the following scenarios:</span></span>  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a><span data-ttu-id="40866-129">Разработка поставщика с симметричным сопоставлением типов</span><span class="sxs-lookup"><span data-stu-id="40866-129">Writing a Provider with Symmetric Type Mapping</span></span>  
 <span data-ttu-id="40866-130">Можно написать поставщик для, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] где каждый тип хранилища сопоставляется с одним типом EDM, независимо от направления сопоставления.</span><span class="sxs-lookup"><span data-stu-id="40866-130">You can write a provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] where each store type maps to a single EDM type, regardless of the mapping direction.</span></span> <span data-ttu-id="40866-131">Для типа поставщика, имеющего простое сопоставление с типом модели EDM, можно использовать симметричное решение, поскольку система типов проста или совпадает с системой типов модели EDM.</span><span class="sxs-lookup"><span data-stu-id="40866-131">For a provider type that has very simple mapping that corresponds with an EDM type, you can use a symmetric solution because the type system is simple or matches EDM types.</span></span>  
  
 <span data-ttu-id="40866-132">В случае простой структуры домена можно создать статический манифест поставщика в декларативном стиле.</span><span class="sxs-lookup"><span data-stu-id="40866-132">You can use the simplicity of their domain and produce a static declarative provider manifest.</span></span>  
  
 <span data-ttu-id="40866-133">Создайте XML-файл с двумя разделами.</span><span class="sxs-lookup"><span data-stu-id="40866-133">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="40866-134">Список типов поставщика в терминах эквивалентов EDM для типа или функции хранилища.</span><span class="sxs-lookup"><span data-stu-id="40866-134">A list of provider types expressed in terms of the "EDM counterpart" of a store type or function.</span></span> <span data-ttu-id="40866-135">Для типов хранилища имеются эквиваленты в модели EDM.</span><span class="sxs-lookup"><span data-stu-id="40866-135">Store types have counterpart EDM types.</span></span> <span data-ttu-id="40866-136">Для функций хранилища имеются соответствующие функции в модели EDM.</span><span class="sxs-lookup"><span data-stu-id="40866-136">Store functions have corresponding EDM functions.</span></span> <span data-ttu-id="40866-137">Например, тип varchar является типом SQL Server, а в модели EDM ему соответствует тип string.</span><span class="sxs-lookup"><span data-stu-id="40866-137">For example, varchar is a SQL Server type but the corresponding EDM type is string.</span></span>  
  
- <span data-ttu-id="40866-138">Список функций, поддерживаемых поставщиком, с указанием типов параметров и возвращаемых значений в терминах модели EDM.</span><span class="sxs-lookup"><span data-stu-id="40866-138">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a><span data-ttu-id="40866-139">Разработка поставщика с асимметричным сопоставлением типов</span><span class="sxs-lookup"><span data-stu-id="40866-139">Writing a Provider with Asymmetric Type Mapping</span></span>  
 <span data-ttu-id="40866-140">При создании поставщика хранилища данных для [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] сопоставление типов между моделью EDM и поставщиком для некоторых типов может отличаться от обратного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="40866-140">When writing a data store provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], the EDM-to-provider type mapping for some types may be different from provider-to-EDM type mapping.</span></span> <span data-ttu-id="40866-141">Например, непривязанный тип EDM PrimitiveTypeKind.String может сопоставляться с типом nvarchar(4000) в поставщике, а тип nvarchar(4000) сопоставляется с типом EDM PrimitiveTypeKind.String(MaxLength=4000).</span><span class="sxs-lookup"><span data-stu-id="40866-141">For instance, unbounded EDM PrimitiveTypeKind.String may map to nvarchar(4000) on the provider, while nvarchar(4000) maps to the EDM PrimitiveTypeKind.String(MaxLength=4000).</span></span>  
  
 <span data-ttu-id="40866-142">Создайте XML-файл с двумя разделами.</span><span class="sxs-lookup"><span data-stu-id="40866-142">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="40866-143">Список типов поставщиков, выраженных в терминах модели EDM и определяющий сопоставление для обоих направлений: EDM-to-provider и provider-to-EDM.</span><span class="sxs-lookup"><span data-stu-id="40866-143">A list of provider types expressed in EDM terms and define mapping for both direction: EDM-to-provider and provider-to-EDM.</span></span>  
  
- <span data-ttu-id="40866-144">Список функций, поддерживаемых поставщиком, с указанием типов параметров и возвращаемых значений в терминах модели EDM.</span><span class="sxs-lookup"><span data-stu-id="40866-144">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
## <a name="provider-manifest-discoverability"></a><span data-ttu-id="40866-145">Возможность обнаружения манифеста поставщика</span><span class="sxs-lookup"><span data-stu-id="40866-145">Provider Manifest Discoverability</span></span>  
 <span data-ttu-id="40866-146">Манифест неявно используется несколькими типами компонентов в службах сущностей (например, средствами и запросами), а также непосредственно используется в метаданных с помощью загрузчика метаданных хранилища.</span><span class="sxs-lookup"><span data-stu-id="40866-146">The manifest is used indirectly by several component types in Entity Services (for example Tools or Query) but more directly leveraged by metadata through the use of the data store metadata loader.</span></span>  
  
 <span data-ttu-id="40866-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span><span class="sxs-lookup"><span data-stu-id="40866-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span></span>  
  
 <span data-ttu-id="40866-148">При этом заданный поставщик может поддерживать различные хранилища или различные версии одного хранилища.</span><span class="sxs-lookup"><span data-stu-id="40866-148">However, a given provider may support different stores or different versions of the same store.</span></span> <span data-ttu-id="40866-149">Поэтому поставщик должен передавать различный манифест для каждого из поддерживаемых хранилищ данных.</span><span class="sxs-lookup"><span data-stu-id="40866-149">Therefore, a provider must report a different manifest for each supported data store.</span></span>  
  
### <a name="provider-manifest-token"></a><span data-ttu-id="40866-150">Маркер манифеста поставщика</span><span class="sxs-lookup"><span data-stu-id="40866-150">Provider Manifest Token</span></span>  
 <span data-ttu-id="40866-151">Если установлено соединение с хранилищем данных, поставщик может запросить сведения, чтобы вернуть правильный манифест.</span><span class="sxs-lookup"><span data-stu-id="40866-151">When a data store connection is opened, the provider can query for information to return the right manifest.</span></span> <span data-ttu-id="40866-152">Это может быть невозможно при автономном использовании, когда недоступны сведения о соединении или невозможно подключиться к хранилищу.</span><span class="sxs-lookup"><span data-stu-id="40866-152">This may not be possible in offline scenarios where connection information is not available or when it is not possible to connect to the store.</span></span> <span data-ttu-id="40866-153">Определите манифест с помощью атрибута `ProviderManifestToken` элемента `Schema` в SSDL-файле.</span><span class="sxs-lookup"><span data-stu-id="40866-153">Identify the manifest by using the `ProviderManifestToken` attribute of the `Schema` element in the .ssdl file.</span></span> <span data-ttu-id="40866-154">Формат этого атрибута не задан жестко. Поставщик выбирает минимально необходимые сведения для определения манифеста без соединения с хранилищем.</span><span class="sxs-lookup"><span data-stu-id="40866-154">There is no required format for this attribute; the provider chooses the minimum information needed to identify a manifest without opening a connection to the store.</span></span>  
  
 <span data-ttu-id="40866-155">Например:</span><span class="sxs-lookup"><span data-stu-id="40866-155">For example:</span></span>  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a><span data-ttu-id="40866-156">Модель программирования манифеста поставщика</span><span class="sxs-lookup"><span data-stu-id="40866-156">Provider Manifest Programming Model</span></span>  
 <span data-ttu-id="40866-157">Поставщики являются производными от класса <xref:System.Data.Common.DbXmlEnabledProviderManifest> и поэтому могут указывать манифесты декларативно.</span><span class="sxs-lookup"><span data-stu-id="40866-157">Providers derive from <xref:System.Data.Common.DbXmlEnabledProviderManifest>, which allows them to specify their manifests declaratively.</span></span> <span data-ttu-id="40866-158">На следующем рисунке показана иерархия классов поставщика.</span><span class="sxs-lookup"><span data-stu-id="40866-158">The following illustration shows the class hierarchy of a provider:</span></span>  
  
 <span data-ttu-id="40866-159">![None](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span><span class="sxs-lookup"><span data-stu-id="40866-159">![None](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span></span>  
  
### <a name="discoverability-api"></a><span data-ttu-id="40866-160">API обнаружения</span><span class="sxs-lookup"><span data-stu-id="40866-160">Discoverability API</span></span>  
 <span data-ttu-id="40866-161">Манифест поставщика загружается загрузчиком метаданных хранилища (StoreItemCollection) с помощью соединения с хранилищем данных или маркера манифеста поставщика.</span><span class="sxs-lookup"><span data-stu-id="40866-161">The provider manifest is loaded by the Store Metadata loader (StoreItemCollection), either by using a data store connection or a provider manifest token.</span></span>  
  
#### <a name="using-a-data-store-connection"></a><span data-ttu-id="40866-162">Использование соединения с хранилищем данных</span><span class="sxs-lookup"><span data-stu-id="40866-162">Using a Data Store Connection</span></span>  
 <span data-ttu-id="40866-163">Если подключение к хранилищу данных доступно, вызовите <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> метод, чтобы вернуть маркер, который передается в этот <xref:System.Data.Common.DbProviderManifest> <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> способ, который возвращает.</span><span class="sxs-lookup"><span data-stu-id="40866-163">When the data store connection is available, call <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> to return the token that is passed to the <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> method, which returns <xref:System.Data.Common.DbProviderManifest>.</span></span> <span data-ttu-id="40866-164">Этот метод делегирует реализацию `GetDbProviderManifestToken`поставщика.</span><span class="sxs-lookup"><span data-stu-id="40866-164">This method delegates to the provider's implementation of `GetDbProviderManifestToken`.</span></span>  
  
```csharp
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a><span data-ttu-id="40866-165">Использование маркера манифеста поставщика</span><span class="sxs-lookup"><span data-stu-id="40866-165">Using a Provider Manifest Token</span></span>  
 <span data-ttu-id="40866-166">В случае автономной работы маркер берется из представления SSDL.</span><span class="sxs-lookup"><span data-stu-id="40866-166">For the offline scenario, the token is picked from SSDL representation.</span></span> <span data-ttu-id="40866-167">Язык SSDL позволяет указать ProviderManifestToken (Дополнительные сведения см. в разделе [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) ).</span><span class="sxs-lookup"><span data-stu-id="40866-167">The SSDL allows you to specify a ProviderManifestToken (see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) for more information).</span></span> <span data-ttu-id="40866-168">Например, если не удается открыть соединение, то в SSDL используется маркер манифеста поставщика, в котором указываются сведения о манифесте.</span><span class="sxs-lookup"><span data-stu-id="40866-168">For example, if a connection cannot be opened, the SSDL has a provider manifest token that specifies information about the manifest.</span></span>  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a><span data-ttu-id="40866-169">Схема манифеста поставщика</span><span class="sxs-lookup"><span data-stu-id="40866-169">Provider Manifest Schema</span></span>  
 <span data-ttu-id="40866-170">Схема данных, определенных для каждого поставщика, содержит статические данные для обработки в метаданных.</span><span class="sxs-lookup"><span data-stu-id="40866-170">The schema of information defined for each provider contains the static information to be consumed by metadata:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema elementFormDefault="qualified"  
   xmlns:xs="http://www.w3.org/2001/XMLSchema"  
   targetNamespace="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest"  
   xmlns:pm="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest">  
  
  <xs:element name="ProviderManifest">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Types" type="pm:TTypes" minOccurs="1" maxOccurs="1" />  
        <xs:element name="Functions" type="pm:TFunctions" minOccurs="0" maxOccurs="1"/>  
      </xs:sequence>  
      <xs:attribute name="Namespace" type="xs:string" use="required"/>  
    </xs:complexType>  
  </xs:element>  
  <xs:complexType name="TVersion">  
    <xs:attribute name="Major" type="xs:int" use="required" />  
    <xs:attribute name="Minor" type="xs:int" use="required" />  
    <xs:attribute name="Build" type="xs:int" use="required" />  
    <xs:attribute name="Revision" type="xs:int" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TIntegerFacetDescription">  
    <xs:attribute name="Minimum" type="xs:int" use="optional" />  
    <xs:attribute name="Maximum" type="xs:int" use="optional" />  
    <xs:attribute name="DefaultValue" type="xs:int" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TBooleanFacetDescription">  
    <xs:attribute name="DefaultValue" type="xs:boolean" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="true" />  
  </xs:complexType>  
  
  <xs:complexType name="TDateTimeFacetDescription">  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TFacetDescriptions">  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="Precision" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Scale" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="MaxLength" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Unicode" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
      <xs:element name="FixedLength" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:complexType name="TType">  
    <xs:sequence>  
      <xs:element name="FacetDescriptions" type="pm:TFacetDescriptions" minOccurs="0" maxOccurs="1"/>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required"/>  
    <xs:attribute name="PrimitiveTypeKind" type="pm:TPrimitiveTypeKind" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TTypes">  
    <xs:sequence>  
      <xs:element name="Type" type="pm:TType" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:attributeGroup name="TFacetAttribute">  
    <xs:attribute name="Precision" type="xs:int" use="optional"/>  
    <xs:attribute name="Scale" type="xs:int" use="optional"/>  
    <xs:attribute name="MaxLength" type="xs:int" use="optional"/>  
    <xs:attribute name="Unicode" type="xs:boolean" use="optional"/>  
    <xs:attribute name="FixedLength" type="xs:boolean" use="optional"/>  
  </xs:attributeGroup>  
  
  <xs:complexType name="TFunctionParameter">  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
    <xs:attribute name="Mode" type="pm:TParameterDirection" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TReturnType">  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunction">  
    <xs:choice minOccurs="0" maxOccurs ="unbounded">  
      <xs:element name ="ReturnType" type="pm:TReturnType" minOccurs="0" maxOccurs="1" />  
      <xs:element name="Parameter" type="pm:TFunctionParameter" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:choice>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Aggregate" type="xs:boolean" use="optional" />  
    <xs:attribute name="BuiltIn" type="xs:boolean" use="optional" />  
    <xs:attribute name="StoreFunctionName" type="xs:string" use="optional" />  
    <xs:attribute name="NiladicFunction" type="xs:boolean" use="optional" />  
    <xs:attribute name="ParameterTypeSemantics" type="pm:TParameterTypeSemantics" use="optional" default="AllowImplicitConversion" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunctions">  
    <xs:sequence>  
      <xs:element name="Function" type="pm:TFunction" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:simpleType name="TPrimitiveTypeKind">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Binary"/>  
      <xs:enumeration value="Boolean"/>  
      <xs:enumeration value="Byte"/>  
      <xs:enumeration value="Decimal"/>  
      <xs:enumeration value="DateTime"/>  
      <xs:enumeration value="Time"/>  
      <xs:enumeration value="DateTimeOffset"/>          
      <xs:enumeration value="Double"/>  
      <xs:enumeration value="Guid"/>  
      <xs:enumeration value="Single"/>  
      <xs:enumeration value="SByte"/>  
      <xs:enumeration value="Int16"/>  
      <xs:enumeration value="Int32"/>  
      <xs:enumeration value="Int64"/>  
      <xs:enumeration value="String"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In"/>  
      <xs:enumeration value="Out"/>  
      <xs:enumeration value="InOut"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterTypeSemantics">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="ExactMatchOnly" />  
      <xs:enumeration value="AllowImplicitPromotion" />  
      <xs:enumeration value="AllowImplicitConversion" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
#### <a name="types-node"></a><span data-ttu-id="40866-171">Узел типов</span><span class="sxs-lookup"><span data-stu-id="40866-171">Types Node</span></span>  
 <span data-ttu-id="40866-172">Узел типов в манифесте поставщика содержит сведения о типах, которые поддерживаются хранилищем данных непосредственно или с помощью поставщика.</span><span class="sxs-lookup"><span data-stu-id="40866-172">The Types node in the provider manifest contains information about the Types that are supported natively by the data store or through the provider.</span></span>  
  
##### <a name="type-node"></a><span data-ttu-id="40866-173">Узел типа</span><span class="sxs-lookup"><span data-stu-id="40866-173">Type Node</span></span>  
 <span data-ttu-id="40866-174">В каждом узле типа определяется тип поставщика в терминах модели EDM.</span><span class="sxs-lookup"><span data-stu-id="40866-174">Each Type node defines a provider type in terms of EDM.</span></span> <span data-ttu-id="40866-175">В узле типа описывается имя типа поставщика и сведения, связанные с типом модели, который сопоставляется с типом поставщика, и с аспектами, описывающими это сопоставление.</span><span class="sxs-lookup"><span data-stu-id="40866-175">The Type node describes the name of the provider type, and information related to the model type it maps to and facets to describe that type mapping.</span></span>  
  
 <span data-ttu-id="40866-176">Для выражения этих сведений о типе в манифесте поставщика каждое определение TypeInformation должно определять несколько аспектов для каждого типа.</span><span class="sxs-lookup"><span data-stu-id="40866-176">In order to express this type information in the provider manifest, each TypeInformation declaration must define several facet descriptions for each Type:</span></span>  
  
|<span data-ttu-id="40866-177">Имя атрибута</span><span class="sxs-lookup"><span data-stu-id="40866-177">Attribute Name</span></span>|<span data-ttu-id="40866-178">Тип данных</span><span class="sxs-lookup"><span data-stu-id="40866-178">Data Type</span></span>|<span data-ttu-id="40866-179">Обязательно</span><span class="sxs-lookup"><span data-stu-id="40866-179">Required</span></span>|<span data-ttu-id="40866-180">Default Value</span><span class="sxs-lookup"><span data-stu-id="40866-180">Default Value</span></span>|<span data-ttu-id="40866-181">Описание</span><span class="sxs-lookup"><span data-stu-id="40866-181">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="40866-182">name</span><span class="sxs-lookup"><span data-stu-id="40866-182">Name</span></span>|<span data-ttu-id="40866-183">String</span><span class="sxs-lookup"><span data-stu-id="40866-183">String</span></span>|<span data-ttu-id="40866-184">Да</span><span class="sxs-lookup"><span data-stu-id="40866-184">Yes</span></span>|<span data-ttu-id="40866-185">Н/Д</span><span class="sxs-lookup"><span data-stu-id="40866-185">n/a</span></span>|<span data-ttu-id="40866-186">Имя типа данных, зависящего от поставщика</span><span class="sxs-lookup"><span data-stu-id="40866-186">Provider-specific data type name</span></span>|  
|<span data-ttu-id="40866-187">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="40866-187">PrimitiveTypeKind</span></span>|<span data-ttu-id="40866-188">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="40866-188">PrimitiveTypeKind</span></span>|<span data-ttu-id="40866-189">Да</span><span class="sxs-lookup"><span data-stu-id="40866-189">Yes</span></span>|<span data-ttu-id="40866-190">Н/Д</span><span class="sxs-lookup"><span data-stu-id="40866-190">n/a</span></span>|<span data-ttu-id="40866-191">Имя типа в модели EDM</span><span class="sxs-lookup"><span data-stu-id="40866-191">EDM type name</span></span>|  
  
###### <a name="function-node"></a><span data-ttu-id="40866-192">Узел функции</span><span class="sxs-lookup"><span data-stu-id="40866-192">Function Node</span></span>  
 <span data-ttu-id="40866-193">В каждом узле функции определяется функция, доступная посредством поставщика.</span><span class="sxs-lookup"><span data-stu-id="40866-193">Each Function defines a single function available through the provider.</span></span>  
  
|<span data-ttu-id="40866-194">Имя атрибута</span><span class="sxs-lookup"><span data-stu-id="40866-194">Attribute Name</span></span>|<span data-ttu-id="40866-195">Тип данных</span><span class="sxs-lookup"><span data-stu-id="40866-195">Data Type</span></span>|<span data-ttu-id="40866-196">Обязательно</span><span class="sxs-lookup"><span data-stu-id="40866-196">Required</span></span>|<span data-ttu-id="40866-197">Default Value</span><span class="sxs-lookup"><span data-stu-id="40866-197">Default Value</span></span>|<span data-ttu-id="40866-198">Описание</span><span class="sxs-lookup"><span data-stu-id="40866-198">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="40866-199">name</span><span class="sxs-lookup"><span data-stu-id="40866-199">Name</span></span>|<span data-ttu-id="40866-200">String</span><span class="sxs-lookup"><span data-stu-id="40866-200">String</span></span>|<span data-ttu-id="40866-201">Да</span><span class="sxs-lookup"><span data-stu-id="40866-201">Yes</span></span>|<span data-ttu-id="40866-202">Н/Д</span><span class="sxs-lookup"><span data-stu-id="40866-202">n/a</span></span>|<span data-ttu-id="40866-203">Идентификатор или имя функции</span><span class="sxs-lookup"><span data-stu-id="40866-203">Identifier/name of the function</span></span>|  
|<span data-ttu-id="40866-204">ReturnType</span><span class="sxs-lookup"><span data-stu-id="40866-204">ReturnType</span></span>|<span data-ttu-id="40866-205">String</span><span class="sxs-lookup"><span data-stu-id="40866-205">String</span></span>|<span data-ttu-id="40866-206">Нет</span><span class="sxs-lookup"><span data-stu-id="40866-206">No</span></span>|<span data-ttu-id="40866-207">Void</span><span class="sxs-lookup"><span data-stu-id="40866-207">Void</span></span>|<span data-ttu-id="40866-208">Тип возвращаемого значения функции в модели EDM</span><span class="sxs-lookup"><span data-stu-id="40866-208">The EDM return type of the function</span></span>|  
|<span data-ttu-id="40866-209">Aggregate</span><span class="sxs-lookup"><span data-stu-id="40866-209">Aggregate</span></span>|<span data-ttu-id="40866-210">логический</span><span class="sxs-lookup"><span data-stu-id="40866-210">Boolean</span></span>|<span data-ttu-id="40866-211">Нет</span><span class="sxs-lookup"><span data-stu-id="40866-211">No</span></span>|<span data-ttu-id="40866-212">False</span><span class="sxs-lookup"><span data-stu-id="40866-212">False</span></span>|<span data-ttu-id="40866-213">Значение True, если функция является агрегатной</span><span class="sxs-lookup"><span data-stu-id="40866-213">True if the function is an aggregate function</span></span>|  
|<span data-ttu-id="40866-214">BuiltIn</span><span class="sxs-lookup"><span data-stu-id="40866-214">BuiltIn</span></span>|<span data-ttu-id="40866-215">логический</span><span class="sxs-lookup"><span data-stu-id="40866-215">Boolean</span></span>|<span data-ttu-id="40866-216">Нет</span><span class="sxs-lookup"><span data-stu-id="40866-216">No</span></span>|<span data-ttu-id="40866-217">True</span><span class="sxs-lookup"><span data-stu-id="40866-217">True</span></span>|<span data-ttu-id="40866-218">Значение True, если функция встроена в хранилище данных</span><span class="sxs-lookup"><span data-stu-id="40866-218">True if the function is built into the data store</span></span>|  
|<span data-ttu-id="40866-219">StoreFunctionName</span><span class="sxs-lookup"><span data-stu-id="40866-219">StoreFunctionName</span></span>|<span data-ttu-id="40866-220">String</span><span class="sxs-lookup"><span data-stu-id="40866-220">String</span></span>|<span data-ttu-id="40866-221">Нет</span><span class="sxs-lookup"><span data-stu-id="40866-221">No</span></span>|<span data-ttu-id="40866-222">\<Имя ></span><span class="sxs-lookup"><span data-stu-id="40866-222">\<Name></span></span>|<span data-ttu-id="40866-223">Имя функции в хранилище данных.</span><span class="sxs-lookup"><span data-stu-id="40866-223">Function Name in the data store.</span></span>  <span data-ttu-id="40866-224">Реализует уровень перенаправления для имен функций.</span><span class="sxs-lookup"><span data-stu-id="40866-224">Allows for a level of redirection of function names.</span></span>|  
|<span data-ttu-id="40866-225">NiladicFunction</span><span class="sxs-lookup"><span data-stu-id="40866-225">NiladicFunction</span></span>|<span data-ttu-id="40866-226">логический</span><span class="sxs-lookup"><span data-stu-id="40866-226">Boolean</span></span>|<span data-ttu-id="40866-227">Нет</span><span class="sxs-lookup"><span data-stu-id="40866-227">No</span></span>|<span data-ttu-id="40866-228">False</span><span class="sxs-lookup"><span data-stu-id="40866-228">False</span></span>|<span data-ttu-id="40866-229">Значение True, если функция не требует параметров и вызывается без параметров</span><span class="sxs-lookup"><span data-stu-id="40866-229">True if the function does not require parameters and is called without any parameters</span></span>|  
|<span data-ttu-id="40866-230">ParameterType</span><span class="sxs-lookup"><span data-stu-id="40866-230">ParameterType</span></span><br /><br /> <span data-ttu-id="40866-231">Семантика</span><span class="sxs-lookup"><span data-stu-id="40866-231">Semantics</span></span>|<span data-ttu-id="40866-232">ParameterSemantics</span><span class="sxs-lookup"><span data-stu-id="40866-232">ParameterSemantics</span></span>|<span data-ttu-id="40866-233">Нет</span><span class="sxs-lookup"><span data-stu-id="40866-233">No</span></span>|<span data-ttu-id="40866-234">AllowImplicit</span><span class="sxs-lookup"><span data-stu-id="40866-234">AllowImplicit</span></span><br /><br /> <span data-ttu-id="40866-235">Преобразование</span><span class="sxs-lookup"><span data-stu-id="40866-235">Conversion</span></span>|<span data-ttu-id="40866-236">Выберите, как конвейер запросов должен обрабатывать замену типов параметров:</span><span class="sxs-lookup"><span data-stu-id="40866-236">Choice of how the query pipeline should deal with parameter type substitution:</span></span><br /><br /> <span data-ttu-id="40866-237">-Ексактматчонли</span><span class="sxs-lookup"><span data-stu-id="40866-237">-   ExactMatchOnly</span></span><br /><span data-ttu-id="40866-238">-АлловимплиЦитпромотион</span><span class="sxs-lookup"><span data-stu-id="40866-238">-   AllowImplicitPromotion</span></span><br /><span data-ttu-id="40866-239">-АлловимплиЦитконверсион</span><span class="sxs-lookup"><span data-stu-id="40866-239">-   AllowImplicitConversion</span></span>|  
  
 <span data-ttu-id="40866-240">**Узел параметров**</span><span class="sxs-lookup"><span data-stu-id="40866-240">**Parameters Node**</span></span>  
  
 <span data-ttu-id="40866-241">Каждая функция имеет коллекцию из одного или нескольких узлов параметров.</span><span class="sxs-lookup"><span data-stu-id="40866-241">Each function has a collection of one or more Parameter nodes.</span></span>  
  
|<span data-ttu-id="40866-242">Имя атрибута</span><span class="sxs-lookup"><span data-stu-id="40866-242">Attribute Name</span></span>|<span data-ttu-id="40866-243">Тип данных</span><span class="sxs-lookup"><span data-stu-id="40866-243">Data Type</span></span>|<span data-ttu-id="40866-244">Обязательно</span><span class="sxs-lookup"><span data-stu-id="40866-244">Required</span></span>|<span data-ttu-id="40866-245">Default Value</span><span class="sxs-lookup"><span data-stu-id="40866-245">Default Value</span></span>|<span data-ttu-id="40866-246">Описание</span><span class="sxs-lookup"><span data-stu-id="40866-246">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="40866-247">name</span><span class="sxs-lookup"><span data-stu-id="40866-247">Name</span></span>|<span data-ttu-id="40866-248">String</span><span class="sxs-lookup"><span data-stu-id="40866-248">String</span></span>|<span data-ttu-id="40866-249">Да</span><span class="sxs-lookup"><span data-stu-id="40866-249">Yes</span></span>|<span data-ttu-id="40866-250">Н/Д</span><span class="sxs-lookup"><span data-stu-id="40866-250">n/a</span></span>|<span data-ttu-id="40866-251">Идентификатор или имя параметра.</span><span class="sxs-lookup"><span data-stu-id="40866-251">Identifier/name of the parameter.</span></span>|  
|<span data-ttu-id="40866-252">Тип</span><span class="sxs-lookup"><span data-stu-id="40866-252">Type</span></span>|<span data-ttu-id="40866-253">String</span><span class="sxs-lookup"><span data-stu-id="40866-253">String</span></span>|<span data-ttu-id="40866-254">Да</span><span class="sxs-lookup"><span data-stu-id="40866-254">Yes</span></span>|<span data-ttu-id="40866-255">Н/Д</span><span class="sxs-lookup"><span data-stu-id="40866-255">n/a</span></span>|<span data-ttu-id="40866-256">Тип параметра в модели EDM.</span><span class="sxs-lookup"><span data-stu-id="40866-256">The EDM type of the parameter.</span></span>|  
|<span data-ttu-id="40866-257">Mode</span><span class="sxs-lookup"><span data-stu-id="40866-257">Mode</span></span>|<span data-ttu-id="40866-258">Параметр</span><span class="sxs-lookup"><span data-stu-id="40866-258">Parameter</span></span><br /><br /> <span data-ttu-id="40866-259">Direction</span><span class="sxs-lookup"><span data-stu-id="40866-259">Direction</span></span>|<span data-ttu-id="40866-260">Да</span><span class="sxs-lookup"><span data-stu-id="40866-260">Yes</span></span>|<span data-ttu-id="40866-261">Н/Д</span><span class="sxs-lookup"><span data-stu-id="40866-261">n/a</span></span>|<span data-ttu-id="40866-262">Направление параметра:</span><span class="sxs-lookup"><span data-stu-id="40866-262">Direction of parameter:</span></span><br /><br /> <span data-ttu-id="40866-263">— в</span><span class="sxs-lookup"><span data-stu-id="40866-263">-   in</span></span><br /><span data-ttu-id="40866-264">-out</span><span class="sxs-lookup"><span data-stu-id="40866-264">-   out</span></span><br /><span data-ttu-id="40866-265">-Inout</span><span class="sxs-lookup"><span data-stu-id="40866-265">-   inout</span></span>|  
  
##### <a name="namespace-attribute"></a><span data-ttu-id="40866-266">Атрибут Namespace</span><span class="sxs-lookup"><span data-stu-id="40866-266">Namespace Attribute</span></span>  
 <span data-ttu-id="40866-267">В каждом поставщике хранилища данных должно определяться пространство имен или группа пространств имен для сведений, определяемых в манифесте.</span><span class="sxs-lookup"><span data-stu-id="40866-267">Each data store provider must define a namespace or group of namespaces for information defined in the manifest.</span></span> <span data-ttu-id="40866-268">Это пространство имен можно использовать в запросах Entity SQL для разрешения имен функций и типов.</span><span class="sxs-lookup"><span data-stu-id="40866-268">This namespace can be used in Entity SQL queries to resolve names of functions and types.</span></span> <span data-ttu-id="40866-269">Например: Server.</span><span class="sxs-lookup"><span data-stu-id="40866-269">For instance: SqlServer.</span></span> <span data-ttu-id="40866-270">Это пространство имен должно отличаться от канонического пространства имен EDM, определенного в службах сущностей для стандартных функций, поддерживаемых запросами Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="40866-270">That namespace must be different from the canonical namespace, EDM, defined by Entity Services for standard functions to be supported by Entity SQL queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40866-271">См. также</span><span class="sxs-lookup"><span data-stu-id="40866-271">See also</span></span>

- [<span data-ttu-id="40866-272">Создание поставщика данных Entity Framework</span><span class="sxs-lookup"><span data-stu-id="40866-272">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
