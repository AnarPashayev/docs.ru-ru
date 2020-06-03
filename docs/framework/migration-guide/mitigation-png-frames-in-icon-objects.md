---
title: Устранение рисков. Кадры PNG в объектах Icon
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: 713e6a0fa615ac748134fac501e5142a65e434f1
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248899"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="4ce20-102">Устранение рисков. Кадры PNG в объектах Icon</span><span class="sxs-lookup"><span data-stu-id="4ce20-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="4ce20-103">начиная с версии .NET Framework 4.6 метод <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> успешно преобразует значки с кадрами PNG в объекты <xref:System.Drawing.Bitmap> .</span><span class="sxs-lookup"><span data-stu-id="4ce20-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="4ce20-104">В приложениях, предназначенных для .NET Framework 4.5.2 и более ранних версий, метод <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> создает исключение <xref:System.ArgumentOutOfRangeException> , если объект <xref:System.Drawing.Icon> содержит кадры PNG.</span><span class="sxs-lookup"><span data-stu-id="4ce20-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="4ce20-105">Последствия</span><span class="sxs-lookup"><span data-stu-id="4ce20-105">Impact</span></span>  
 <span data-ttu-id="4ce20-106">Это изменение затрагивает приложения, которые компилируются повторно для платформы .NET Framework 4.6 и в которых реализуется специальная обработка исключения <xref:System.ArgumentOutOfRangeException> , создаваемого при наличии кадров PNG в объекте <xref:System.Drawing.Icon> .</span><span class="sxs-lookup"><span data-stu-id="4ce20-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="4ce20-107">При выполнении в .NET Framework 4.6 преобразование проходит успешно, исключение <xref:System.ArgumentOutOfRangeException> больше не создается, и поэтому обработчик исключений больше не вызывается.</span><span class="sxs-lookup"><span data-stu-id="4ce20-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="4ce20-108">Устранение рисков</span><span class="sxs-lookup"><span data-stu-id="4ce20-108">Mitigation</span></span>  
 <span data-ttu-id="4ce20-109">Если такое поведение нежелательно, можно сохранить прежнее поведение, добавив в раздел [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) файла app.config следующий элемент:</span><span class="sxs-lookup"><span data-stu-id="4ce20-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="4ce20-110">Если файл app.config уже содержит элемент `AppContextSwitchOverrides`, новое значение следует объединить с атрибутом `value` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="4ce20-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;previous key=previous-value" />
```
  
## <a name="see-also"></a><span data-ttu-id="4ce20-111">См. также</span><span class="sxs-lookup"><span data-stu-id="4ce20-111">See also</span></span>

- [<span data-ttu-id="4ce20-112">Совместимость приложений</span><span class="sxs-lookup"><span data-stu-id="4ce20-112">Application compatibility</span></span>](application-compatibility.md)
