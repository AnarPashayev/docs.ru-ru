---
title: Критические изменения в Windows Forms
description: Список критических изменений в Windows Forms для .NET Core и .NET 5.
ms.date: 09/08/2020
ms.openlocfilehash: 3e7d077d07203d9c231ae4a7805e593c5432c135
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679008"
---
# <a name="breaking-changes-in-windows-forms"></a>Критические изменения в Windows Forms

Поддержка Windows Forms была добавлена в .NET Core в версии 3.0. В этой статье перечислены критические изменения для Windows Forms, сгруппированные по версии .NET, в которой они появились. Если вы обновляете приложение Windows Forms с .NET Framework или с предыдущей версии .NET Core (3.0 или более поздней), эта статья для вас актуальна.

На этой странице описаны следующие критические изменения:

| Критическое изменение | Представленная версия |
| - | :-: |
| [Свойству OutputType задано значение WinExe для приложений WPF и WinForms](#outputtype-set-to-winexe-for-wpf-and-winforms-apps) | 5.0 |
| [API, связанные с DataGridView, теперь вызывают исключение InvalidOperationException](#datagridview-related-apis-now-throw-invalidoperationexception) | 5.0 |
| [В приложениях WinForms и WPF используется Microsoft.NET.Sdk](#winforms-and-wpf-apps-use-microsoftnetsdk) | 5.0 |
| [Удалены элементы управления строкой состояния](#removed-status-bar-controls) | 5.0 |
| [Теперь методы WinForms вызывают исключение ArgumentException](#winforms-methods-now-throw-argumentexception) | 5.0 |
| [Теперь методы WinForms вызывают исключение ArgumentNullException](#winforms-methods-now-throw-argumentnullexception) | 5.0 |
| [Теперь свойства WinForms вызывают исключение ArgumentOutOfRangeException](#winforms-properties-now-throw-argumentoutofrangeexception) | 5.0 |
| [Удаленные элементы управления](#removed-controls) | 3.1 |
| [При отображении подсказки не возникает событие CellFormatting](#cellformatting-event-not-raised-if-tooltip-is-shown) | 3.1 |
| [Шрифт Control.DefaultFont изменен на Segoe UI 9 пт](#default-control-font-changed-to-segoe-ui-9-pt) | 3.0 |
| [Модернизация FolderBrowserDialog](#modernization-of-the-folderbrowserdialog) | 3.0 |
| [Из некоторых типов Windows Forms удален атрибут SerializableAttribute](#serializableattribute-removed-from-some-windows-forms-types) | 3.0 |
| [Параметр совместимости AllowUpdateChildControlIndexForTabControls не поддерживается](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | 3.0 |
| [Параметр совместимости DomainUpDown.UseLegacyScrolling не поддерживается](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | 3.0 |
| [Параметр совместимости DoNotLoadLatestRichEditControl не поддерживается](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | 3.0 |
| [Параметр совместимости DoNotSupportSelectAllShortcutInMultilineTextBox не поддерживается](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | 3.0 |
| [Параметр совместимости DontSupportReentrantFilterMessage не поддерживается](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | 3.0 |
| [Параметр совместимости EnableVisualStyleValidation не поддерживается](#enablevisualstylevalidation-compatibility-switch-not-supported) | 3.0 |
| [Параметр совместимости UseLegacyContextMenuStripSourceControlValue не поддерживается](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | 3.0 |
| [Параметр совместимости UseLegacyImages не поддерживается](#uselegacyimages-compatibility-switch-not-supported) | 3.0 |

## <a name="net-50"></a>.NET 5.0

[!INCLUDE [automatically-infer-winexe-output-type](../../../includes/core-changes/windowsforms/5.0/automatically-infer-winexe-output-type.md)]

***

[!INCLUDE [null-owner-causes-invalidoperationexception](../../../includes/core-changes/windowsforms/5.0/null-owner-causes-invalidoperationexception.md)]

***

[!INCLUDE [sdk-and-target-framework-change](../../../includes/core-changes/windowsforms/5.0/sdk-and-target-framework-change.md)]

***

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

***

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

***

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

[!INCLUDE [invalid-args-cause-argumentoutofrangeexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentoutofrangeexception.md)]

***

## <a name="net-core-31"></a>.NET Core 3.1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

## <a name="see-also"></a>См. также

- [Перенос приложения Windows Forms в .NET Core](../porting/winforms.md)
