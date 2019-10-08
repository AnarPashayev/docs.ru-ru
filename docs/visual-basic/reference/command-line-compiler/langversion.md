---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 15f334f280c2aca83ba5b628a1137464c31c6282
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005552"
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
Приводит к тому, что компилятор принимает только синтаксис, включенный в указанную языковую версию Visual Basic.  
  
## <a name="syntax"></a>Синтаксис  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a>Аргументы  
 `version`  
 Обязательный. Языковая версия, используемая во время компиляции. Допустимые значения: `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` и `latest`.

 Любое из целых чисел можно также указать с помощью `.0` в качестве дополнительной версии, например `11.0`.

 Чтобы просмотреть список всех возможных значений, укажите `-langversion:?` в командной строке.  
  
## <a name="remarks"></a>Примечания  
 Параметр `-langversion` указывает синтаксис, принимаемый компилятором. Например, если указать, что языковая версия — 9,0, компилятор выдает ошибки для синтаксиса, который допустим только в версии 10,0 и более поздних версиях.  
  
 Этот параметр можно использовать при разработке приложений, предназначенных для разных версий .NET Framework. Например, если вы нацелены на .NET Framework 3,5, можно использовать этот параметр, чтобы не использовать синтаксис из языковой версии 10,0.  
  
 Вы можете установить `-langversion` напрямую только с помощью командной строки. Дополнительные сведения см. в разделе [Указание конкретной версии или профиля .NET Framework](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).  
  
## <a name="example"></a>Пример  
 Следующий код компилирует `sample.vb` для Visual Basic 9,0.  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>См. также

- [Компилятор Visual Basic с интерфейсом командной строки](../../../visual-basic/reference/command-line-compiler/index.md)
- [Примеры командных строк компиляции](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Настройка конкретной версии платформы .NET Framework](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
