---
title: EXCEPTION_STATE Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd2e280cd03ae413e0853950d13fbfefb69bc15f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736958"
---
# <a name="exception_state"></a>EXCEPTION_STATE
Определяет состояние исключения.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
typedef DWORD EXCEPTION_STATE;
```

```csharp
public enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
```

## <a name="fields"></a>Поля
`EXCEPTION_NONE`\
Не останавливайтесь на исключении.

`EXCEPTION_STOP_FIRST_CHANCE`\
Остановите при первом запуске исключения. При описании события исключения этот флаг указывает, что событие исключения является событием исключения первого шанса.

`EXCEPTION_STOP_SECOND_CHANCE`\
Остановка на второй стрельбе исключения. При описании события исключения указывается, что событие исключения является событием исключения второй случайности.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Остановите при первом запуске исключения пользовательского режима. При описании события исключения указывается, что событие исключения является событием исключения пользователя первого шанса.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Остановка, когда исключение пользовательского режима не поймано. При описании события исключения указывается, что событие исключения является непойманным событием исключения пользовательского режима.

`EXCEPTION_STOP_ALL`\
Остановитесь на любом исключении. Не используется при описании события исключения.

`EXCEPTION_CANNOT_BE_CONTINUED`\
При описании события исключения указывается, что исключение не может быть продолжено.

`EXCEPTION_CODE_SUPPORTED`\
Означает, что в исключении есть код, поддерживающий его. Используется при отображении исключения

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Означает, что код исключения должен отображаться в гексадецимальном. Используется при отображении исключения.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Указывается, что код исключения поддерживает JustMyCode. Используется при отображении исключения.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Указано, что управляемый отладчик кода должен обрабатывать исключения. Если не установить, отладчик по умолчанию обрабатывает исключения. Это передается методу [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) и не используется в [структуре EXCEPTION_INFO.](../../../extensibility/debugger/reference/exception-info.md)

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
УСТАРЕВШИЕ, НЕ ИСПОЛЬЗОВАТЬ.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
УСТАРЕВШИЕ, НЕ ИСПОЛЬЗОВАТЬ.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
УСТАРЕВШИЕ, НЕ ИСПОЛЬЗОВАТЬ.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
УСТАРЕВШИЕ, НЕ ИСПОЛЬЗОВАТЬ.

## <a name="remarks"></a>Примечания
Используется в `dwState` качестве члена [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) структуры для указания состояния исключения и что можно с делать с ним.

Эти значения также передаются методу [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) для настройки состояния всех исключений.

Эти флаги могут быть объединены с bitwise OR.

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
