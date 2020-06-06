---
title: Схема параметров приложения
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2020
ms.locfileid: "81242833"
---
# <a name="application-settings-schema"></a><span data-ttu-id="c15c4-102">Схема параметров приложения</span><span class="sxs-lookup"><span data-stu-id="c15c4-102">Application Settings schema</span></span>

<span data-ttu-id="c15c4-103">Параметры приложения позволяют Windows Forms или ASP.NET приложению сохранять и извлекать параметры приложения и области пользователя.</span><span class="sxs-lookup"><span data-stu-id="c15c4-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="c15c4-104">В этом контексте *параметр* — это любой фрагмент информации, который может быть специфичен для приложения или зависит от текущего пользователя — от строки подключения к базе данных до предпочитаемого пользователем размера окна по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c15c4-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="c15c4-105">По умолчанию параметры приложения в Windows Formsном приложении используют <xref:System.Configuration.LocalFileSettingsProvider> класс, который использует систему конфигурации .NET для хранения параметров в XML-файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c15c4-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="c15c4-106">Дополнительные сведения о файлах, используемых параметрами приложения, см. в разделе [архитектура параметров приложения](../../winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="c15c4-106">For more information about the files used by application settings, see [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="c15c4-107">Параметры приложения определяют следующие элементы в составе файлов конфигурации, которые он использует.</span><span class="sxs-lookup"><span data-stu-id="c15c4-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="c15c4-108">Элемент</span><span class="sxs-lookup"><span data-stu-id="c15c4-108">Element</span></span>                    | <span data-ttu-id="c15c4-109">Описание</span><span class="sxs-lookup"><span data-stu-id="c15c4-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | <span data-ttu-id="c15c4-110">Содержит все **\<setting>** теги, характерные для приложения.</span><span class="sxs-lookup"><span data-stu-id="c15c4-110">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| **\<userSettings>**        | <span data-ttu-id="c15c4-111">Содержит все **\<setting>** теги, относящиеся к текущему пользователю.</span><span class="sxs-lookup"><span data-stu-id="c15c4-111">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| **\<setting>**             | <span data-ttu-id="c15c4-112">Определяет параметр.</span><span class="sxs-lookup"><span data-stu-id="c15c4-112">Defines a setting.</span></span> <span data-ttu-id="c15c4-113">Дочерний элемент либо **\<applicationSettings>** или **\<userSettings>** .</span><span class="sxs-lookup"><span data-stu-id="c15c4-113">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| **\<value>**               | <span data-ttu-id="c15c4-114">Определяет значение параметра.</span><span class="sxs-lookup"><span data-stu-id="c15c4-114">Defines a setting's value.</span></span> <span data-ttu-id="c15c4-115">Дочерний элемент **\<setting>** .</span><span class="sxs-lookup"><span data-stu-id="c15c4-115">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="c15c4-116">Элемент \<applicationSettings></span><span class="sxs-lookup"><span data-stu-id="c15c4-116">\<applicationSettings> element</span></span>

<span data-ttu-id="c15c4-117">Этот элемент содержит все **\<setting>** теги, характерные для экземпляра приложения на клиентском компьютере.</span><span class="sxs-lookup"><span data-stu-id="c15c4-117">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="c15c4-118">Атрибуты не определяются.</span><span class="sxs-lookup"><span data-stu-id="c15c4-118">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="c15c4-119">Элемент \<userSettings></span><span class="sxs-lookup"><span data-stu-id="c15c4-119">\<userSettings> element</span></span>

<span data-ttu-id="c15c4-120">Этот элемент содержит все **\<setting>** теги, характерные для пользователя, который в настоящее время использует приложение.</span><span class="sxs-lookup"><span data-stu-id="c15c4-120">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="c15c4-121">Атрибуты не определяются.</span><span class="sxs-lookup"><span data-stu-id="c15c4-121">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="c15c4-122">\<setting> - элемент</span><span class="sxs-lookup"><span data-stu-id="c15c4-122">\<setting> element</span></span>

<span data-ttu-id="c15c4-123">Этот элемент определяет параметр.</span><span class="sxs-lookup"><span data-stu-id="c15c4-123">This element defines a setting.</span></span> <span data-ttu-id="c15c4-124">Он имеет следующие атрибуты.</span><span class="sxs-lookup"><span data-stu-id="c15c4-124">It has the following attributes.</span></span>

| <span data-ttu-id="c15c4-125">Атрибут</span><span class="sxs-lookup"><span data-stu-id="c15c4-125">Attribute</span></span>        | <span data-ttu-id="c15c4-126">Описание</span><span class="sxs-lookup"><span data-stu-id="c15c4-126">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="c15c4-127">**name**</span><span class="sxs-lookup"><span data-stu-id="c15c4-127">**name**</span></span>         | <span data-ttu-id="c15c4-128">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="c15c4-128">Required.</span></span> <span data-ttu-id="c15c4-129">Уникальный идентификатор параметра.</span><span class="sxs-lookup"><span data-stu-id="c15c4-129">The unique ID of the setting.</span></span> <span data-ttu-id="c15c4-130">Параметры, созданные в Visual Studio, сохраняются с именем `ProjectName.Properties.Settings` .</span><span class="sxs-lookup"><span data-stu-id="c15c4-130">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="c15c4-131">**serializeAs**</span><span class="sxs-lookup"><span data-stu-id="c15c4-131">**serializeAs**</span></span> | <span data-ttu-id="c15c4-132">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="c15c4-132">Required.</span></span> <span data-ttu-id="c15c4-133">Формат, используемый для сериализации значения в текст.</span><span class="sxs-lookup"><span data-stu-id="c15c4-133">The format to use for serializing the value to text.</span></span> <span data-ttu-id="c15c4-134">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="c15c4-134">Valid values are:</span></span><br><br><span data-ttu-id="c15c4-135">- `string`.</span><span class="sxs-lookup"><span data-stu-id="c15c4-135">- `string`.</span></span> <span data-ttu-id="c15c4-136">Значение сериализуется в виде строки с помощью <xref:System.ComponentModel.TypeConverter> .</span><span class="sxs-lookup"><span data-stu-id="c15c4-136">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="c15c4-137">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="c15c4-137">- `xml`.</span></span> <span data-ttu-id="c15c4-138">Значение сериализуется с помощью сериализации XML.</span><span class="sxs-lookup"><span data-stu-id="c15c4-138">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="c15c4-139">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="c15c4-139">- `binary`.</span></span> <span data-ttu-id="c15c4-140">Значение сериализуется как двоичный файл, закодированный в виде текста, с помощью двоичной сериализации.</span><span class="sxs-lookup"><span data-stu-id="c15c4-140">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="c15c4-141">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="c15c4-141">- `custom`.</span></span> <span data-ttu-id="c15c4-142">Поставщик параметров обладает знаниями об этом параметре и сериализует и десериализует его.</span><span class="sxs-lookup"><span data-stu-id="c15c4-142">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="c15c4-143">\<value> - элемент</span><span class="sxs-lookup"><span data-stu-id="c15c4-143">\<value> element</span></span>

<span data-ttu-id="c15c4-144">Этот элемент содержит значение параметра.</span><span class="sxs-lookup"><span data-stu-id="c15c4-144">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="c15c4-145">Пример</span><span class="sxs-lookup"><span data-stu-id="c15c4-145">Example</span></span>

<span data-ttu-id="c15c4-146">В следующем примере показан файл параметров приложения, который определяет два параметра области приложения и два параметра уровня пользователя:</span><span class="sxs-lookup"><span data-stu-id="c15c4-146">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c15c4-147">См. также</span><span class="sxs-lookup"><span data-stu-id="c15c4-147">See also</span></span>

- [<span data-ttu-id="c15c4-148">Общие сведения о параметрах приложений</span><span class="sxs-lookup"><span data-stu-id="c15c4-148">Application Settings Overview</span></span>](../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="c15c4-149">Архитектура параметров приложения</span><span class="sxs-lookup"><span data-stu-id="c15c4-149">Application Settings Architecture</span></span>](../../winforms/advanced/application-settings-architecture.md)
