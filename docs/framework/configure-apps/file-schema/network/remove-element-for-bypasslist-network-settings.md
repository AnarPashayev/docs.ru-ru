---
title: Элемент <remove> для bypasslist (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: a04cca3e57af5cc422776c5b2444a140e86f98b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674471"
---
# <a name="remove-element-for-bypasslist-network-settings"></a>\<Удалить > элемент для bypasslist (параметры сети)

Удаляет IP-адрес или DNS-имя из списка обхода прокси-сервера.

\<Конфигурация > \
\<System.NET > \
\<defaultProxy > \
\<bypasslist > \
\<Удалить >

## <a name="syntax"></a>Синтаксис

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы

В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|**Attribute (XElement Dynamic Property)** (Attribute (динамическое свойство XElement))|**Описание**|
|-------------------|---------------------|
|`address`|Регулярное выражение, описывающее IP-адрес или DNS-имя.|

### <a name="child-elements"></a>Дочерние элементы

Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|**Элемент**|**Описание**|
|-----------------|---------------------|
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Предоставляет набор регулярных выражений, описывающих адреса, которые не используют прокси-сервер.|

## <a name="remarks"></a>Примечания

`remove` Приводит к удалению регулярное выражение, описывающее IP-адреса или имена DNS-серверов в списке адресов, которые обходят прокси-сервер. Эти адреса были заданы ранее в файле конфигурации или на более высоком уровне в иерархии конфигурации.

Значение для `address` атрибут должен быть регулярное выражение, которое описывает набор IP-адресов или имен узлов.

Дополнительные сведения о регулярных выражениях см. в разделе. [Регулярные выражения .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).

## <a name="configuration-files"></a>Файлы конфигурации

Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).

## <a name="example"></a>Пример

Следующий пример отменяет любые предыдущие определения для домена adventure-works.com и затем добавляется в список пропускаемых домен contoso.com.

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <bypasslist>
        <remove address="[a-z]+\.adventure-works\.com$" />
        <add address="[a-z]+\.contoso\.com$" />
      </bypasslist>
    </defaultProxy>
  </system.net>
</configuration>
```

## <a name="see-also"></a>См. также

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Схема параметров сети](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
