---
ms.openlocfilehash: 1545c807e3bef675e63e14d01ab82c1131600f39
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804893"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear не удаляет дубликаты из SelectedItems

|   |   |
|---|---|
|Подробные сведения|Если в элементе Selector, поддерживающем выбор нескольких элементов, в коллекции <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> присутствуют дубликаты, один и тот же элемент присутствует несколько раз.  Удаление этих элементов из источника данных (например, путем вызова Items.Clear) не приведет к их удалению из коллекции <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>. Будет удален только первый экземпляр. Более того, последующее использование коллекции <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>, например вызов SelectedItems.Clear(), может вызвать проблемы, например исключение <xref:System.ArgumentException?displayProperty=name>, так как коллекция <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> содержит элементы, которые отсутствуют в источнике данных.|
|Предложение|По возможности выполните обновление до .NET 4.6.2.|
|Область|Дополнительный номер|
|Версия|4.5|
|Тип|Среда выполнения|
|Затронутые API|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|
