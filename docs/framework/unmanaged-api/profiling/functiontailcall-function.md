---
title: Функция FunctionTailcall
ms.date: 03/30/2017
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 656f2498c7dd9ba165ab6759d8ca3b26e0d7c93f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598783"
---
# <a name="functiontailcall-function"></a>Функция FunctionTailcall
Уведомляет профилировщик о том, что текущей выполняемой функции собирается выполнить вызов с префиксом tail в другую функцию.  
  
> [!NOTE]
>  `FunctionTailcall` Рекомендуется использовать функцию в .NET Framework версии 2.0. Она будет продолжать работать, но будет привести к снижению производительности. Используйте [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) вместо этого функцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `funcID`  
 [in] Идентификатор текущей выполняемой функции, который собираетесь сделать с префиксом tail.  
  
## <a name="remarks"></a>Примечания  
 Целевая функция вызова с префиксом tail будет использовать текущий кадр стека и возвращает непосредственно вызывающему объекту функции, внесенные с префиксом tail. Это означает, что [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) обратного вызова не выдается для функции, которая является целевым объектом вызова с префиксом tail.  
  
 `FunctionTailcall` Функция является обратным вызовом; это необходимо реализовать. В реализации должен использоваться `__declspec`(`naked`) атрибут класса хранения.  
  
 Ядро выполнения не сохраняет значения регистров перед вызовом этой функции.  
  
- При входе необходимо сохранить все регистры, которые вы используете, включая те, в единицах с плавающей запятой (FPU).  
  
- При выходе необходимо восстановить стек путем выталкивания из всех параметров, которые были отправлены вызывающим кодом.  
  
 Реализация `FunctionTailcall` не должен блокироваться, поскольку это приведет к задержке сборки мусора. Реализация не должны сбор мусора, так как стек может находиться в состоянии коллекции с поддержкой сборки мусора. При попытке сбора мусора, среда выполнения будет блокироваться до `FunctionTailcall` возвращает.  
  
 Кроме того `FunctionTailcall` функция не должна вызывать управляемый код или каким-либо образом вызывать управляемое распределение памяти.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorProf.idl  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>См. также

- [Функция FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [Функция FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [Метод SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Глобальные статические функции профилирования](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
