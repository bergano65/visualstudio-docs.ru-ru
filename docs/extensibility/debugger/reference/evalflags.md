---
title: ЭВАЛЕСЕС Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4136726e5c8b798121dbd38975d8f2bb935ed04a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737109"
---
# <a name="evalflags"></a>EVALFLAGS
Определяет флаги, контролирующие оценку выражения.

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

## <a name="fields"></a>Поля
`EVAL_RETURNVALUE`\
Упомяните, что значение возврата, если таковое, будет оценено.

`EVAL_NOSIDEEFFECTS`\
Упомянет, что побочные эффекты не допускаются.

`EVAL_ALLOWBPS`\
Определяет остановку на брейк-пойнтах.

`EVAL_ALLOWERRORREPORT`\
Упогоняет разрешение сообщения об ошибке к усею. В первую очередь используется для оценки выражения в скрипте в Internet Explorer.

`EVAL_FUNCTION_AS_ADDRESS`\
Функции сил должны оцениваться как адреса, а не ссылаться на функцию.

`EVAL_NOFUNCEVAL`\
Предотвращает оценку функции. Например, рассмотрим `int` маркер в `myExpression(int) + 10`выражении . Эту функцию можно правильно оценить как адрес, но не как значение.

`EVAL_NOEVENTS`\
Пометить, чтобы указать, что события, возникающие во время оценки выражения, не должны отправляться менеджеру отладки сеанса (SDM) или IDE.

## <a name="remarks"></a>Примечания
Эти флаги передаются в качестве аргумента методам [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) и [EvaluateSync.](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)

Эти флаги могут быть объединены с bitwise OR.

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
