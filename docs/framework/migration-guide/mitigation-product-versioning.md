---
title: Устранение рисков. Управление версиями продукта
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8811fd916afcb39c466b8c9a60f7c7ed2a62ea8
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301441"
---
# <a name="mitigation-product-versioning"></a>Устранение рисков. Управление версиями продукта
В .NET Framework 4.6 и более поздних версиях управление версиями продукта отличается от предыдущих выпусков платформы .NET Framework (.NET Framework 4, 4.5, 4.5.1 и 4.5.2).  
  
## <a name="product-versioning-changes"></a>Изменения управления версиями продукта  
 Ниже приведено подробное описание изменений.  
  
- Значение записи `Version` в разделе `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` изменилось на `4.6.`*xxxxx* в .NET Framework 4.6 и ее доработанных версиях и на `4.7.`*xxxxx* в .NET Framework 4.7. В .NET Framework 4.5, 4.5.1 и 4.5.2 использовался формат `4.5.`*xxxxx*.  
  
- Управление версиями файлов и продукта для файлов .NET Framework было изменено с более ранней схемы управления версиями `4.0.30319.x` на `4.6.X.0` для .NET Framework 4.6 и ее доработанных выпусков, а также на `4.7.X.0` для .NET Framework 4.7 и ее доработанных выпусков. Вы можете увидеть эти новые значения в **свойствах** файла, щелкнув файл правой кнопкой мыши.  
  
- Атрибуты <xref:System.Reflection.AssemblyFileVersionAttribute> и <xref:System.Reflection.AssemblyInformationalVersionAttribute> для управляемых сборок имеют значения <xref:System.Version> в виде `4.6.X.0` на платформе .NET Framework 4.6 и в ее доработанных выпусках или `4.7.X.0` на платформе .NET Framework 4.7.  
  
- В .NET Framework 4.6, 4.6.1, 4.6.2 и 4.7 свойство <xref:System.Environment.Version%2A?displayProperty=nameWithType> возвращает исправленную строку версии `4.0.30319.42000`. В .NET Framework 4, 4.5, 4.5.1 и 4.5.2 оно возвращает строки версии в формате `4.0.30319.xxxxx` (например, "4.0.30319.18010"). Обратите внимание, что создание в свойстве <xref:System.Environment.Version%2A?displayProperty=nameWithType> новых зависимостей от кода приложения не рекомендуется.  
  
### <a name="handling-the-product-versioning-changes"></a>Обработка изменений управления версиями продукта  
 В общем случае приложения для обнаружения таких сведений, как версия среды выполнения .NET Framework и каталог установки, должны использовать следующие рекомендуемые методы:  
  
- Чтобы определить версию среды выполнения .NET Framework, см. статью [Практическое руководство. Определение установленных версий платформы .NET Framework](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).  
  
- Чтобы определить путь установки платформы .NET Framework, используйте значение записи `InstallPath` в ключе `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`.  
  
    > [!IMPORTANT]
    >  Имя подраздела — `NET Framework Setup`, а не `.NET Framework Setup`.  
  
- Чтобы определить путь к каталогу общеязыковой среды выполнения .NET Framework, вызовите метод <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType>.  
  
- Чтобы получить версию среды CLR, вызовите метод <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType>.   Для .NET Framework 4 и ее доработанных выпусков (.NET Framework 4.5, 4.5.1, 4.5.2 и .NET Framework 4.6, 4.6.1, 4.6.2 и 4.7) возвращается строка `v4.0.30319`.  
  
## <a name="see-also"></a>См. также

- [Изменения среды выполнения](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
