---
title: Элемент <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102896"
---
# <a name="gccpugroup-element"></a>Элемент \<GCCpuGroup>

Определяет, поддерживает ли сборка мусора несколько групп ЦП.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**

## <a name="syntax"></a>Синтаксис

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы

В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`enabled`|Обязательный атрибут.<br /><br /> Определяет, поддерживает ли сборка мусора несколько групп ЦП.|

## <a name="enabled-attribute"></a>Атрибут enabled

|Значение|Описание|
|-----------|-----------------|
|`false`|Сборка мусора не поддерживает несколько групп ЦП. Это значение по умолчанию.|
|`true`|Сборка мусора поддерживает несколько групп ЦП, если включена сборка мусора сервера.|

### <a name="child-elements"></a>Дочерние элементы

Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|`configuration`|Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.|
|`runtime`|Содержит сведения о привязке сборок и сборке мусора.|

## <a name="remarks"></a>Примечания

Если на компьютере установлено несколько групп ЦП и включена сборка мусора сервера (см. [\<gcServer>](gcserver-element.md) элемент), включение этого элемента расширяет сбор мусора во всех группах ЦП и учитывает все ядра при создании и балансировке куч.

> [!NOTE]
> Этот элемент применяется только к потокам сборки мусора. Чтобы среда выполнения распространяла пользовательские потоки во всех группах ЦП, необходимо также включить [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) элемент.

## <a name="example"></a>Пример

В следующем примере показано, как включить сбор мусора для нескольких групп ЦП.

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>См. также

- [Схема параметров среды выполнения](index.md)
- [Схема файла конфигурации](../index.md)
- [Отключение параллельной сборки мусора](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Сборка мусора рабочей станции и сборка мусора сервера](../../../../standard/garbage-collection/workstation-server-gc.md)
