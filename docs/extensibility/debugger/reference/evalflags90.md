---
title: ЭВАЛЕСЕС90 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01951885541ba4acce33f3e4f06f7106116ccc62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737102"
---
# <a name="evalflags90"></a>EVALFLAGS90
Перечисляет допустимые значения для флагов, контролирующих оценку выражения. Этот пересчет расширяет перечисление [EVALFLAGS.](../../../extensibility/debugger/reference/evalflags.md)

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
typedef DWORD EVALFLAGS90;
```

```csharp
public enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
```

## <a name="fields"></a>Поля
`EVAL90_RETURNVALUE`\
Упомяните, что значение возврата, если таковое, будет оценено.

`EVAL90_NOSIDEEFFECTS`\
Упомянет, что побочные эффекты не допускаются.

`EVAL90_ALLOWBPS`\
Определяет остановку на брейк-пойнтах.

`EVAL90_ALLOWERRORREPORT`\
Упоньте, что сообщение об ошибке к усту будет разрешено. В первую очередь используется для оценки выражения в скрипте в Internet Explorer.

`EVAL90_FUNCTION_AS_ADDRESS`\
Функции сил должны оцениваться как адреса, а не ссылаться на функцию.

`EVAL90_NOFUNCEVAL`\
Предотвращает оценку функции. Например, рассмотрим `int` маркер в `myExpression(int) + 10`выражении . Эту функцию можно правильно оценить как адрес, но не как значение.

`EVAL90_NOEVENTS`\
Пометить, чтобы указать, что события, возникающие во время оценки выражения, не должны отправляться менеджеру отладки сеанса (SDM) или IDE.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
Позволяет проводить оценку экспрессии времени проектирования.

`EVAL90_ALLOW_IMPLICIT_VARS`\
Позволяет неявное создание переменной.

`EVAL90_FORCE_EVALUATION_NOW`\
Оценка сил произойдет немедленно. Это полезно при обслуживании запроса, например, запроса пользователя.

## <a name="requirements"></a>Требования
Заголовок: Msdbg90.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
