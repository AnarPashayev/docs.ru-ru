---
title: Практическое руководство. Воспроизведение сигнала в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], beep
- Windows Forms, sounds
- sounds [Windows Forms], playing
- forms [Windows Forms], sounds
- examples [Windows Forms], sounds
ms.assetid: 7ea5cded-4888-4f35-8f28-5cab1a55c973
ms.openlocfilehash: 0aa01f600873dd8853e1c33d5443448835e11455
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146228"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a><span data-ttu-id="bf68d-102">Практическое руководство. Воспроизведение сигнала в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bf68d-102">How to: Play a Beep from a Windows Form</span></span>
<span data-ttu-id="bf68d-103">В этом примере воспроизводится звуковой сигнал во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="bf68d-103">This example plays a beep at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf68d-104">Пример</span><span class="sxs-lookup"><span data-stu-id="bf68d-104">Example</span></span>  
  
```vb  
Public Sub OnePing()  
    Beep()  
End Sub  
```  
  
```csharp  
public void onePing()  
{  
    SystemSounds.Beep.Play();  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="bf68d-105">Звук, воспроизводимый в C# пример кода определяется <xref:System.Media.SystemSounds.Beep%2A> параметр системы.</span><span class="sxs-lookup"><span data-stu-id="bf68d-105">The sound played in the C# code sample is determined by the <xref:System.Media.SystemSounds.Beep%2A> system sound setting.</span></span> <span data-ttu-id="bf68d-106">Дополнительные сведения см. в разделе <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="bf68d-106">For more information, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bf68d-107">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="bf68d-107">Compiling the Code</span></span>  
 <span data-ttu-id="bf68d-108">Для C#, в этом примере требуется ссылка на <xref:System.Media?displayProperty=nameWithType> пространства имен.</span><span class="sxs-lookup"><span data-stu-id="bf68d-108">For C#, this example requires  a reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf68d-109">См. также</span><span class="sxs-lookup"><span data-stu-id="bf68d-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="bf68d-110">Практическое руководство. Воспроизведение системных звуков в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bf68d-110">How to: Play a System Sound from a Windows Form</span></span>](how-to-play-a-system-sound-from-a-windows-form.md)
- [<span data-ttu-id="bf68d-111">Практическое руководство. Воспроизведение звука в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bf68d-111">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
