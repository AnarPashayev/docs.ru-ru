---
title: Практическое руководство. Создание параметров приложения
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
ms.openlocfilehash: 5cf109aec8b55650f43f07f5b303c6373df4efc7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305979"
---
# <a name="how-to-create-application-settings"></a><span data-ttu-id="84ec5-102">Практическое руководство. Создание параметров приложения</span><span class="sxs-lookup"><span data-stu-id="84ec5-102">How to: Create Application Settings</span></span>
<span data-ttu-id="84ec5-103">С помощью управляемого кода можно создавать параметры приложения и привязывать их к свойствам формы или ее элементов управления, чтобы эти параметры загружались и сохранялись автоматически во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="84ec5-103">Using managed code, you can create new application settings and bind them to properties on your form or your form's controls, so that these settings are loaded and saved automatically at run time.</span></span>  
  
 <span data-ttu-id="84ec5-104">В представленной ниже процедуре вручную создается класс-оболочка, производный от класса <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="84ec5-104">In the following procedure, you manually create a wrapper class that derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span> <span data-ttu-id="84ec5-105">К этому классу добавляется открытое свойство для каждого параметра приложения, который требуется предоставить.</span><span class="sxs-lookup"><span data-stu-id="84ec5-105">To this class you add a publicly accessible property for each application setting that you want to expose.</span></span>  
  
 <span data-ttu-id="84ec5-106">Эту процедуру можно также выполнить с помощью минимального объема кода в конструкторе Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="84ec5-106">You can also perform this procedure using minimal code in the Visual Studio designer.</span></span>  <span data-ttu-id="84ec5-107">Также см. раздел [Как Создание параметров приложения с помощью конструктора](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/wabtadw6(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="84ec5-107">Also see [How to: Create Application Settings Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/wabtadw6(v=vs.100)).</span></span>  
  
### <a name="to-create-new-application-settings-programmatically"></a><span data-ttu-id="84ec5-108">Создание параметров приложения программными средствами</span><span class="sxs-lookup"><span data-stu-id="84ec5-108">To create new Application Settings programmatically</span></span>  
  
1. <span data-ttu-id="84ec5-109">Добавьте в проект новый класс и переименуйте его.</span><span class="sxs-lookup"><span data-stu-id="84ec5-109">Add a new class to your project, and rename it.</span></span> <span data-ttu-id="84ec5-110">Для выполнения этой процедуры мы назовем этот класс `MyUserSettings`.</span><span class="sxs-lookup"><span data-stu-id="84ec5-110">For this procedure, we will call this class `MyUserSettings`.</span></span> <span data-ttu-id="84ec5-111">Измените определение класса так, чтобы он стал производным от <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="84ec5-111">Change the class definition so that the class derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span>  
  
2. <span data-ttu-id="84ec5-112">Определите в этом классе-оболочке свойство для каждого требуемого параметра приложения и примените его с атрибутом <xref:System.Configuration.ApplicationScopedSettingAttribute> или <xref:System.Configuration.UserScopedSettingAttribute> в зависимости от области действия параметра.</span><span class="sxs-lookup"><span data-stu-id="84ec5-112">Define a property on this wrapper class for each application setting you require, and apply that property with either the <xref:System.Configuration.ApplicationScopedSettingAttribute> or <xref:System.Configuration.UserScopedSettingAttribute>, depending on the scope of the setting.</span></span> <span data-ttu-id="84ec5-113">Дополнительные сведения об области действия параметров см. в разделе [Общие сведения о параметрах приложения](application-settings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="84ec5-113">For more information about settings scope, see [Application Settings Overview](application-settings-overview.md).</span></span> <span data-ttu-id="84ec5-114">На этом этапе код должен выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="84ec5-114">By now, your code should look like this:</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3. <span data-ttu-id="84ec5-115">Создайте экземпляр этого класса-оболочки в приложении.</span><span class="sxs-lookup"><span data-stu-id="84ec5-115">Create an instance of this wrapper class in your application.</span></span> <span data-ttu-id="84ec5-116">Как правило, он является закрытым членом главной формы.</span><span class="sxs-lookup"><span data-stu-id="84ec5-116">It will commonly be a private member of the main form.</span></span> <span data-ttu-id="84ec5-117">Определив класс, нужно привязать его к свойству, в данном случае к свойству <xref:System.Windows.Forms.Form.BackColor%2A> формы.</span><span class="sxs-lookup"><span data-stu-id="84ec5-117">Now that you have defined your class, you need to bind it to a property; in this case, the <xref:System.Windows.Forms.Form.BackColor%2A> property of your form.</span></span> <span data-ttu-id="84ec5-118">Это можно сделать в вашей форме `Load` обработчик событий.</span><span class="sxs-lookup"><span data-stu-id="84ec5-118">You can accomplish this in your form's `Load` event handler.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="84ec5-119">Если вы предоставляете возможность изменения параметров во время выполнения, необходимо сохранять текущие параметры пользователя на диск при закрытии формы, иначе изменения будут потеряны.</span><span class="sxs-lookup"><span data-stu-id="84ec5-119">If you provide a way to change settings at run time, you will need to save the user's current settings to disk when your form closes, or else these changes will be lost.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#3](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     <span data-ttu-id="84ec5-120">Теперь новый параметр приложения успешно создан и связан с указанным свойством.</span><span class="sxs-lookup"><span data-stu-id="84ec5-120">You have now successfully created a new application setting and bound it to the specified property.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="84ec5-121">Безопасность платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="84ec5-121">.NET Framework Security</span></span>  
 <span data-ttu-id="84ec5-122">Поставщик параметров по умолчанию, <xref:System.Configuration.LocalFileSettingsProvider>, сохраняет сведения в файлах конфигурации в виде обычного текста.</span><span class="sxs-lookup"><span data-stu-id="84ec5-122">The default settings provider, <xref:System.Configuration.LocalFileSettingsProvider>, persists information to configuration files as plain text.</span></span> <span data-ttu-id="84ec5-123">В результате безопасность зависит от уровня разрешений на доступ к файлу, предоставляемого операционной системой текущему пользователю.</span><span class="sxs-lookup"><span data-stu-id="84ec5-123">This limits security to the file access security provided by the operating system for the current user.</span></span> <span data-ttu-id="84ec5-124">Поэтому при хранении информации в файлах конфигурации необходимо соблюдать осторожность.</span><span class="sxs-lookup"><span data-stu-id="84ec5-124">Because of this, care must be taken with the information stored in configuration files.</span></span> <span data-ttu-id="84ec5-125">Например, параметры приложения часто используются для хранения строк подключений, которые указывают на хранилище данных приложения.</span><span class="sxs-lookup"><span data-stu-id="84ec5-125">For example, one common use for application settings is to store connection strings that point to the application's data store.</span></span> <span data-ttu-id="84ec5-126">Однако в целях безопасности в таких строках не должны содержаться пароли.</span><span class="sxs-lookup"><span data-stu-id="84ec5-126">However, because of security concerns, such strings should not include passwords.</span></span> <span data-ttu-id="84ec5-127">Подробнее о строках подключения см. в разделе <xref:System.Configuration.SpecialSetting>.</span><span class="sxs-lookup"><span data-stu-id="84ec5-127">For more information about connection strings, see <xref:System.Configuration.SpecialSetting>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84ec5-128">См. также</span><span class="sxs-lookup"><span data-stu-id="84ec5-128">See also</span></span>

- <xref:System.Configuration.SpecialSettingAttribute>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [<span data-ttu-id="84ec5-129">Общие сведения о параметрах приложений</span><span class="sxs-lookup"><span data-stu-id="84ec5-129">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="84ec5-130">Практическое руководство. Проверка параметров приложения</span><span class="sxs-lookup"><span data-stu-id="84ec5-130">How to: Validate Application Settings</span></span>](how-to-validate-application-settings.md)
