---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216927"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>Атрибут SerializableAttribute удален из некоторых типов Windows Forms

Атрибут <xref:System.SerializableAttribute> был удален из некоторых классов Windows Forms, для которых нет известных сценариев двоичной сериализации.

#### <a name="change-description"></a>Описание изменений

Следующие типы помечаются в .NET Framework атрибутом <xref:System.SerializableAttribute>, который удален в .NET Core:

- `System.InvariantComparer`
- <xref:System.ComponentModel.Design.ExceptionCollection?displayProperty=nameWithType>
- <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerException?displayProperty=nameWithType>
- `System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService.CodeDomSerializationStore`
- <xref:System.Drawing.Design.ToolboxItem?displayProperty=nameWithType>
- `System.Resources.ResXNullRef`
- `System.Resources.ResXDataNode`
- `System.Resources.ResXFileRef`
- <xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>
- `System.Windows.Forms.NativeMethods.MSOCRINFOSTRUCT`
- `System.Windows.Forms.NativeMethods.MSG`

Механизм сериализации всегда имел серьезные проблемы в плане обслуживания и безопасности. Поддержка `SerializableAttribute` для типов означает, что их необходимо проверять на наличие изменений сериализации в разных версиях, а также, возможно, на разных платформах. Это затрудняет развитие таких типов и делает их обслуживание затратнее. Для этих типов нет известных сценариев двоичной сериализации, благодаря чему удаление атрибута имеет минимальные последствия.

Дополнительные сведения см. в разделе [Двоичная сериализация](~/docs/standard/serialization/binary-serialization.md).

#### <a name="version-introduced"></a>Представленная версия

3.0, предварительная версия 9

#### <a name="recommended-action"></a>Рекомендуемое действие

Измените код, работа которого зависит от возможности сериализации этих типов.

#### <a name="category"></a>Категория

Windows Forms

#### <a name="affected-apis"></a>Затронутые API

- Нет

<!--

### Affected APIs

- Not detectable via API analysis

-->
