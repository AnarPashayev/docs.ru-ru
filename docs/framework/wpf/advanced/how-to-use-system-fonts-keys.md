---
title: Практическое руководство. Использование разделов системных шрифтов
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: e924f4c14d98380d9f4c0defe27d9f98c3293114
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001615"
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="301d0-102">Практическое руководство. Использование разделов системных шрифтов</span><span class="sxs-lookup"><span data-stu-id="301d0-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="301d0-103">Системные ресурсы предоставляют ряд метрик системы в качестве ресурсов, что помогает разработчикам создавать визуальные элементы, совместимые с параметрами системы.</span><span class="sxs-lookup"><span data-stu-id="301d0-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="301d0-104"><xref:System.Windows.SystemFonts> — Это класс, который содержит значения системных шрифтов и ресурсы системных шрифтов, которые привязаны к значениям — например, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> и <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="301d0-104"><xref:System.Windows.SystemFonts> is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="301d0-105">Метрики системных шрифтов могут использоваться в качестве статического или динамического ресурса.</span><span class="sxs-lookup"><span data-stu-id="301d0-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="301d0-106">Используйте динамический ресурс, если требуется метрика шрифта для автоматического обновления во время выполнения приложения. В противном случае используйте статический ресурс.</span><span class="sxs-lookup"><span data-stu-id="301d0-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="301d0-107">Динамические ресурсы имеют ключевое слово *ключ* добавляется к имени свойства.</span><span class="sxs-lookup"><span data-stu-id="301d0-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="301d0-108">В приведенном ниже примере показано, как получить доступ к ресурсам динамических системных шрифтов и использовать их для создания стиля или настройки кнопки.</span><span class="sxs-lookup"><span data-stu-id="301d0-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="301d0-109">Это [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] примере создается стиль кнопки, который назначает <xref:System.Windows.SystemFonts> значения к кнопке.</span><span class="sxs-lookup"><span data-stu-id="301d0-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="301d0-110">Пример</span><span class="sxs-lookup"><span data-stu-id="301d0-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="301d0-111">См. также</span><span class="sxs-lookup"><span data-stu-id="301d0-111">See also</span></span>

- [<span data-ttu-id="301d0-112">Заливка области с помощью системной кисти</span><span class="sxs-lookup"><span data-stu-id="301d0-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="301d0-113">Использование SystemParameters</span><span class="sxs-lookup"><span data-stu-id="301d0-113">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="301d0-114">Использование SystemFonts</span><span class="sxs-lookup"><span data-stu-id="301d0-114">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
