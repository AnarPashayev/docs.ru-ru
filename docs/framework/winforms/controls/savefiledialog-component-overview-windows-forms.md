---
title: Общие сведения о компоненте SaveFileDialog (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: 1e4269129f17c10056af2765c7a0e74537918ae5
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211610"
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="27405-102">Общие сведения о компоненте SaveFileDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="27405-102">SaveFileDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="27405-103">Компонент Windows Forms <xref:System.Windows.Forms.SaveFileDialog> является стандартным диалоговым окном.</span><span class="sxs-lookup"><span data-stu-id="27405-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="27405-104">Это так же, как стандартный **сохранить файл** диалоговое окно, используемое с Windows.</span><span class="sxs-lookup"><span data-stu-id="27405-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="27405-105">Он наследуется от класса <xref:System.Windows.Forms.CommonDialog>.</span><span class="sxs-lookup"><span data-stu-id="27405-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="27405-106">Работа с помощью компонента SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="27405-106">Working with the SaveFileDialog Component</span></span>

<span data-ttu-id="27405-107">Компонент используется в качестве простого решения для пользователям сохранять файлы вместо того чтобы настраивать собственные диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="27405-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="27405-108">Опираясь на стандартные диалоговые окна Windows, основные функциональные возможности приложения, созданные хорошо знакомы пользователям.</span><span class="sxs-lookup"><span data-stu-id="27405-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="27405-109">Однако имейте в виду, что при с помощью <xref:System.Windows.Forms.SaveFileDialog> компонента, необходимо написать свою собственную логику для сохранения файлов.</span><span class="sxs-lookup"><span data-stu-id="27405-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>

<span data-ttu-id="27405-110">Можно использовать <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> метод, чтобы отобразить диалоговое окно во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="27405-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="27405-111">Файл можно открыть в режиме чтения и записи с помощью <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="27405-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>

<span data-ttu-id="27405-112">При добавлении в форму, <xref:System.Windows.Forms.SaveFileDialog> компонент появится в области в нижней части конструктора Windows Forms в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="27405-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="27405-113">См. также</span><span class="sxs-lookup"><span data-stu-id="27405-113">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="27405-114">Компонент SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="27405-114">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)
