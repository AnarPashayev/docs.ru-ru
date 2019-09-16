---
title: CorFlags.exe (средство преобразования CorFlags)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4228da6efe22091c86de95d846c14f504d51457f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851285"
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (средство преобразования CorFlags)
Средство преобразования CorFlags позволяет настраивать раздел CorFlags в заголовке переносимого исполняемого образа.  
  
 Эта программа автоматически устанавливается вместе с Visual Studio. Чтобы применить этот инструмент, воспользуйтесь командной строкой разработчика для Visual Studio (или командной строкой Visual Studio в Windows 7). Дополнительные сведения см. в разделе [Командные строки](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 В командной строке введите следующее.  
  
## <a name="syntax"></a>Синтаксис  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a>Параметры  
  
|Обязательный параметр|ОПИСАНИЕ|  
|------------------------|-----------------|  
|`assembly`|Имя сборки, для которой требуется настроить раздел CorFlags.|  
  
|Параметр|ОПИСАНИЕ|  
|------------|-----------------|  
|**/32BIT[REQ]+**|Устанавливает флаг 32BITREQUIRED.|  
|**/32BIT[REQ]-**|Снимает флаг 32BITREQUIRED.|  
|**/32BITPREF+**|Устанавливает флаг 32BITPREFERRED. Приложение выполняется как 32-разрядный процесс даже на 64-разрядных платформах. Устанавливайте этот флаг только в EXE-файлах. Если флаг установлен для библиотеки DLL, она не загружается в 64-разрядных процессах и создается исключение <xref:System.BadImageFormatException>. Файл EXE с этим флагом можно загрузить в 64-разрядный процесс.<br /><br /> Новые возможности .NET Framework 4.5.|  
|**/32BITPREF-**|Снимает флаг 32BITPREFERRED.<br /><br /> Новые возможности .NET Framework 4.5.|  
|**/?**|Отображает синтаксис команд и параметров программы.|  
|**/Force**|Выполняет принудительное обновление, даже если сборка имеет строгое имя. **Внимание!**  При обновлении сборки со строгим именем перед выполнением ее кода необходимо снова подписать сборку.|  
|**/help**|Отображает синтаксис команд и параметров программы.|  
|**/ILONLY+**|Устанавливает флаг ILONLY.|  
|**/ILONLY-**|Снимает флаг ILONLY.|  
|**/nologo**|Отключает отображение эмблемы Майкрософт при запуске.|  
|**/RevertCLRHeader**|Задает версии заголовка CLR значение 2.0.|  
|**/ UpgradeCLRHeader**|Обновляет версию заголовка CLR до версии 2.5. **Примечание.**  Для оптимального выполнения сборок они должны иметь версию заголовка CLR 2.5.|  
  
## <a name="remarks"></a>Примечания  
 Если другие параметры не заданы, средство преобразования CorFlags отображает флаги заданной сборки.  
  
## <a name="see-also"></a>См. также

- [Инструменты](../../../docs/framework/tools/index.md)
- [64-разрядные приложения](../../../docs/framework/64-bit-apps.md)
- [Командные строки](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
