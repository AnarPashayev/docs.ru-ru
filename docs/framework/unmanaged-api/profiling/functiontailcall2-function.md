---
title: Функция FunctionTailcall2
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 06dd3b028f4f43ca8681c80a5caa4716104068dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598809"
---
# <a name="functiontailcall2-function"></a>Функция FunctionTailcall2
Уведомляет профилировщик, что текущей выполняемой функции собирается выполнить вызов с префиксом tail в другую функцию и предоставляет сведения о кадре стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `funcId`  
 [in] Идентификатор текущей выполняемой функции, который собираетесь сделать с префиксом tail.  
  
 `clientData`  
 [in] Функция пересопоставленный идентификатора, который ранее указано профилировщик с помощью [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), текущей выполняемой функции, которая является внесем в него с префиксом tail.  
  
 `func`  
 [in] Объект `COR_PRF_FRAME_INFO` значение, которое указывает на сведения о кадре стека.  
  
 Профилировщик должен интерпретировать его как непрозрачный дескриптор, который может быть передан в модуль выполнения в [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) метод.  
  
## <a name="remarks"></a>Примечания  
 Целевая функция вызова с префиксом tail будет использовать текущий кадр стека и возвращает непосредственно вызывающему объекту функции, внесенные с префиксом tail. Это означает, что [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) обратного вызова не выдается для функции, которая является целевым объектом вызова с префиксом tail.  
  
 Значение `func` недопустимый параметр после `FunctionTailcall2` функция возвращает, так как значение, могут быть изменены или удалены.  
  
 `FunctionTailcall2` Функция является обратным вызовом; это необходимо реализовать. В реализации должен использоваться `__declspec`(`naked`) атрибут класса хранения.  
  
 Ядро выполнения не сохраняет значения регистров перед вызовом этой функции.  
  
- При входе необходимо сохранить все регистры, которые вы используете, включая те, в единицах с плавающей запятой (FPU).  
  
- При выходе необходимо восстановить стек путем выталкивания из всех параметров, которые были отправлены вызывающим кодом.  
  
 Реализация `FunctionTailcall2` не должен блокироваться, поскольку это приведет к задержке сборки мусора. Реализация не должны сбор мусора, так как стек может находиться в состоянии коллекции с поддержкой сборки мусора. При попытке сбора мусора, среда выполнения будет блокироваться до `FunctionTailcall2` возвращает.  
  
 Кроме того `FunctionTailcall2` функция не должна вызывать управляемый код или каким-либо образом вызывать управляемое распределение памяти.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorProf.idl  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Функция FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [Функция FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [Метод SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Глобальные статические функции профилирования](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
