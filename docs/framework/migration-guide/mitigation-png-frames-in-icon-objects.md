---
title: Устранение рисков. Кадры PNG в объектах Icon
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85a76681cf6efd649fe366a68d956246334975fe
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789972"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="8cb74-102">Устранение рисков. Кадры PNG в объектах Icon</span><span class="sxs-lookup"><span data-stu-id="8cb74-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="8cb74-103">начиная с версии .NET Framework 4.6 метод <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> успешно преобразует значки с кадрами PNG в объекты <xref:System.Drawing.Bitmap> .</span><span class="sxs-lookup"><span data-stu-id="8cb74-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="8cb74-104">В приложениях, предназначенных для .NET Framework 4.5.2 и более ранних версий, метод <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> создает исключение <xref:System.ArgumentOutOfRangeException> , если объект <xref:System.Drawing.Icon> содержит кадры PNG.</span><span class="sxs-lookup"><span data-stu-id="8cb74-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="8cb74-105">Последствия</span><span class="sxs-lookup"><span data-stu-id="8cb74-105">Impact</span></span>  
 <span data-ttu-id="8cb74-106">Это изменение затрагивает приложения, которые компилируются повторно для платформы .NET Framework 4.6 и в которых реализуется специальная обработка исключения <xref:System.ArgumentOutOfRangeException> , создаваемого при наличии кадров PNG в объекте <xref:System.Drawing.Icon> .</span><span class="sxs-lookup"><span data-stu-id="8cb74-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="8cb74-107">При выполнении в .NET Framework 4.6 преобразование проходит успешно, исключение <xref:System.ArgumentOutOfRangeException> больше не создается, и поэтому обработчик исключений больше не вызывается.</span><span class="sxs-lookup"><span data-stu-id="8cb74-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="8cb74-108">Устранение рисков</span><span class="sxs-lookup"><span data-stu-id="8cb74-108">Mitigation</span></span>  
 <span data-ttu-id="8cb74-109">Если такое поведение нежелательно, можно сохранить прежнее поведение, добавив в раздел [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) файла app.config следующий элемент:</span><span class="sxs-lookup"><span data-stu-id="8cb74-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="8cb74-110">Если файл app.config уже содержит элемент `AppContextSwitchOverrides`, новое значение следует объединить с атрибутом `value` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8cb74-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="8cb74-111">См. также</span><span class="sxs-lookup"><span data-stu-id="8cb74-111">See also</span></span>

- [<span data-ttu-id="8cb74-112">Изменение целевой платформы</span><span class="sxs-lookup"><span data-stu-id="8cb74-112">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
