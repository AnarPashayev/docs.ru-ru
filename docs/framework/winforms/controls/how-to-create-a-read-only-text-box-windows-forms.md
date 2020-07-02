---
title: Практическое руководство. Создание текстового поля только для чтения
description: Узнайте, как преобразовать Редактируемое текстовое поле Windows Forms в текстовое поле Windows Forms только для чтения.
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 5baa7c66d5f16560a4ea23861d563b099592957f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619368"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="cc9db-103">Практическое руководство. Создание текстового поля, доступного только для чтения (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="cc9db-103">How to: Create a Read-Only Text Box (Windows Forms)</span></span>

<span data-ttu-id="cc9db-104">Можно преобразовать редактируемое Windows Forms текстовое поле в элемент управления только для чтения.</span><span class="sxs-lookup"><span data-stu-id="cc9db-104">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="cc9db-105">Например, текстовое поле может отображать значение, которое обычно редактируется, но может не быть в данный момент из-за состояния приложения.</span><span class="sxs-lookup"><span data-stu-id="cc9db-105">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>

## <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="cc9db-106">Создание текстового поля, доступного только для чтения</span><span class="sxs-lookup"><span data-stu-id="cc9db-106">To create a read-only text box</span></span>

1. <span data-ttu-id="cc9db-107">Присвойте <xref:System.Windows.Forms.TextBox> свойству элемента управления значение <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> `true` .</span><span class="sxs-lookup"><span data-stu-id="cc9db-107">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="cc9db-108">Если свойство имеет значение `true` , пользователи по-прежнему могут прокручивать и выделять текст в текстовом поле, не разрешая изменения.</span><span class="sxs-lookup"><span data-stu-id="cc9db-108">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="cc9db-109">Команда **копирования** работает в текстовом поле, но команды **вырезания** и **вставки** не используются.</span><span class="sxs-lookup"><span data-stu-id="cc9db-109">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>

    > [!NOTE]
    > <span data-ttu-id="cc9db-110"><xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>Свойство влияет только на взаимодействие с пользователем во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="cc9db-110">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="cc9db-111">Вы по-прежнему можете изменить содержимое текстового поля программно во время выполнения, изменив <xref:System.Windows.Forms.TextBox.Text%2A> свойство текстового поля.</span><span class="sxs-lookup"><span data-stu-id="cc9db-111">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc9db-112">См. также</span><span class="sxs-lookup"><span data-stu-id="cc9db-112">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="cc9db-113">Общие сведения об элементе управления TextBox</span><span class="sxs-lookup"><span data-stu-id="cc9db-113">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="cc9db-114">Практическое руководство. Управление положением курсора в элементе управления TextBox в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc9db-114">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="cc9db-115">Практическое руководство. Создание текстового поля для ввода пароля с помощью элемента управления TextBox в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc9db-115">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="cc9db-116">Практическое руководство. Добавление кавычек в строку</span><span class="sxs-lookup"><span data-stu-id="cc9db-116">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="cc9db-117">Практическое руководство. Выделение текста в элементе управления TextBox в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc9db-117">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="cc9db-118">Практическое руководство. Многострочные элементы управления TextBox в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc9db-118">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="cc9db-119">Элемент управления TextBox</span><span class="sxs-lookup"><span data-stu-id="cc9db-119">TextBox Control</span></span>](textbox-control-windows-forms.md)
