---
ms.openlocfilehash: b736ab743a628fdcbc53c5ee51551e5dad986885
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888145"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>Событие CellFormatting не возникает при отображении подсказки

<xref:System.Windows.Forms.DataGridView> теперь отображает всплывающие подсказки для ошибок и текста в ячейке при наведении указателя мыши и при выборе с помощью клавиатуры. Если подсказка отображается, событие <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> не возникает.

#### <a name="change-description"></a>Описание изменений

До .NET Core 3.1 <xref:System.Windows.Forms.DataGridView>, у которого для свойства <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> было задано значение `true`, отображал подсказку для ошибок и текста в ячейке при наведении указателя мыши на эту ячейку. Подсказки не отображались при выборе ячейки с помощью клавиатуры (например, с помощью клавиши TAB, сочетаний клавиш или клавиш со стрелками). Если пользователь изменил ячейку, а затем, пока <xref:System.Windows.Forms.DataGridView> находился в режиме редактирования, навел указатель на ячейку, для которой не задано свойство <xref:System.Windows.Forms.DataGridViewCell.ToolTipText>, возникало событие <xref:System.Windows.Forms.DataGridView.CellFormatting> для форматирования текста ячейки, отображаемого в ней.

Чтобы удовлетворить требованиям стандартов специальных возможностей, начиная с .NET Core 3.1, <xref:System.Windows.Forms.DataGridView>, у которого для свойства <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> задано значение `true`, отображает подсказки для ошибок и текста ячейки не только при наведении указателя мыши, но и при выборе ячейки с помощью клавиатуры. Как следствие этого изменения событие <xref:System.Windows.Forms.DataGridView.CellFormatting>*не* возникает, когда указатель наводится на ячейки, для которых не задано свойство <xref:System.Windows.Forms.DataGridViewCell.ToolTipText>, пока <xref:System.Windows.Forms.DataGridView> находится в режиме редактирования. Событие не возникает, так как содержимое ячейки, на которую наведен указатель, выводится в виде подсказки, а не отображается в ячейке.

#### <a name="version-introduced"></a>Представленная версия

3.1

#### <a name="recommended-action"></a>Рекомендованное действие

Выполните рефакторинг всего кода, зависящего от события <xref:System.Windows.Forms.DataGridView.CellFormatting>, когда <xref:System.Windows.Forms.DataGridView> находится в режиме редактирования.

#### <a name="category"></a>Категория

Windows Forms

#### <a name="affected-apis"></a>Затронутые API

Отсутствуют

<!-- 

### Affected APIs

Not detectable via API analysis.

-->
