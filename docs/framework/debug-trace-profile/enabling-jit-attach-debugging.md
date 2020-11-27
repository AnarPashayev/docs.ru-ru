---
title: Включение отладки с JIT-присоединением (трассировка событий Windows)
description: Включить отладку JIT-подключения для подключения отладчика к процессу при возникновении ошибок. Он может вызываться определенными методами или функциями.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
ms.openlocfilehash: dc1c8608b0d16e618b5ad6144d492db3302532dc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273507"
---
# <a name="enabling-jit-attach-debugging"></a>Включение отладки с JIT-присоединением (трассировка событий Windows)

Отладка с JIT-присоединением предусматривает присоединение отладчика к процессу при возникновении ошибок. Также этот процесс может запускаться посредством определенных методов или функций.  
  
 Отладка с JIT-присоединением используется при следующих условиях сбоя:  
  
- Необработанные исключения (в машинном и управляемом коде).  
  
- Метод <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> или функция [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) (семейство ОС Windows 7).  
  
- Неустранимые ошибки времени выполнения.  
  
 Отладка с JIT-присоединением также запускается посредством вызова следующих методов и функций:  
  
- Метод <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>.  
  
- Метод <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>.  
  
- Функция [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) (Win32).  
  
 Перед .NET Framework 4 в .NET Framework предоставлены отдельные разделы реестра для управления поведением отладчиков машинного и управляемого кода. Начиная с .NET Framework 4, управление консолидируется в одном разделе реестра: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Значения этого раздела определяют, будет ли вызываться отладчик, а также будет ли в случае его вызова отображаться диалоговое окно для взаимодействия с пользователем. Сведения об установке этого раздела реестра см. в разделе [Настройка автоматической отладки](/windows/win32/debug/configuring-automatic-debugging).  
  
## <a name="see-also"></a>См. также

- [Отладка, трассировка и профилирование](index.md)
- [Упрощение отладки образов](making-an-image-easier-to-debug.md)
