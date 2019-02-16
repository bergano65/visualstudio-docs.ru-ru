---
title: EVALFLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f780f06188d738deeb7f4b781fba1313e46db6d
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315772"
---
# <a name="evalflags"></a>EVALFLAGS
Указывает флаги, определяющие вычисления выражения.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
};
typedef DWORD EVALFLAGS;
```

```csharp
public enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
}
```

## <a name="members"></a>Участники
EVAL_RETURNVALUE  
Указывает, что возвращаемое значение, если таковое имеется, вычисляется.

EVAL_NOSIDEEFFECTS  
Указывает, что побочные эффекты не разрешается.

EVAL_ALLOWBPS  
Указывает остановки точек останова.

EVAL_ALLOWERRORREPORT  
Указывает отчетов к узлу разрешен об ошибках. В основном используется для вычисления выражений в скрипте в Internet Explorer.

EVAL_FUNCTION_AS_ADDRESS  
Функции силы для оценки в качестве адреса, вместо вызова функции.

EVAL_NOFUNCEVAL  
Запрещает вычисляется функция. Например, рассмотрим `int` маркера в выражении `myExpression(int) + 10`. Эта функция может вычисляться правильно, как адрес, а не как значение.

EVAL_NOEVENTS  
Флаг, указывающий, что события, происходящие во время вычисления выражения не следует отправлять в диспетчер отладки сеансов (SDM) или в интегрированную среду разработки.

## <a name="remarks"></a>Примечания
Эти флаги передаются в качестве аргумента [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) и [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) методы.

Эти флаги могут быть объединены с помощью побитового логического Сложения.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
[Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)  
[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
