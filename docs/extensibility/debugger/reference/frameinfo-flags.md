---
title: FRAMEINFO_FLAGS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3510726400623c5ddf3e7a4d58a4903763b91245
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736796"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
Определяет информацию для получения объекта кадра стека.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
typedef DWORD FRAMEINFO_FLAGS;
```

```csharp
public enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
```

## <a name="fields"></a>Поля
`FIF_FUNCNAME`\
Инициализация/использование `m_bstrFuncName` поля.

`FIF_RETURNTYPE`\
Инициализация/использование `m_bstrReturnType` поля.

`FIF_ARGS`\
Инициализация/использование `m_bstrArgs` поля.

`FIF_LANGUAGE`\
Инициализация/использование `m_bstrLanguage` поля.

`FIF_MODULE`\
Инициализация/использование `m_bstrModule` поля.

`FIF_STACKRANGE`\
Инициализация/использование полей `m_addrMin` и `m_addrMax` (диапазона стеков).

`FIF_FRAME`\
Инициализация/использование `m_pFrame` поля.

`FIF_DEBUGINFO`\
Инициализация/использование `m_fHasDebugInfo` поля.

`FIF_STALECODE`\
Инициализация/использование `m_fStaleCode` поля.

`FIF_ANNOTATEDFRAME`\
Инициализация/использование `m_fAnnotatedFrame` поля.

`FIF_DEBUG_MODULEP`\
Инициализация/использование `m_pModule` поля.

`FIF_FUNCNAME_FORMAT`\
Форматирует имя функции. Результат возвращается в `m_bstrFunName` поле, и никакие другие поля не заполняются.

`FIF_FUNCNAME_RETURNTYPE`\
Добавляет тип возврата `m_bstrFuncName` в поле.

`FIF_FUNCNAME_ARGS`\
Добавляет аргументы в `m_bstrFuncName` поле.

`FIF_FUNCNAME_LANGUAGE`\
Добавляет язык в `m_bstrFuncName` поле.

`FIF_FUNCNAME_MODULE`\
Добавляет имя модуля в `m_bstrFuncName` поле.

`FIF_FUNCNAME_LINES`\
Добавляет количество строк в `m_bstrFuncName` поле.

`FIF_FUNCNAME_OFFSET`\
Добавляет к `m_bstrFuncName` полю смещение в байтах `FIF_FUNCNAME_LINES` от начала линии, если указано. Если `FIF_FUNCNAME_LINES` не указаны, или если номера строк недоступны, добавляет смещение в байтах с самого начала функции.

`FIF_FUNCNAME_ARGS_TYPES`\
Добавляет тип аргумента каждой `m_bstrFuncName` функции в поле.

`FIF_FUNCNAME_ARGS_NAMES`\
Добавляет имя каждого аргумента `m_bstrFuncName` функции в поле.

`FIF_FUNCNAME_ARGS_VALUES`\
Добавляет значение каждого аргумента `m_bstrFuncName` функции в поле.

`FIF_FUNCNAME_ARGS_ALL`\
Добавляет тип, имя и значение всех аргументов в `m_bstrFuncName` поле.

`FIF_ARGS_TYPES`\
Типы аргументов извлекаются и отформатированы.

`FIF_ARGS_NAMES`\
Имена аргументов извлекаются и отформатированы.

`FIF_ARGS_VALUES`\
Значения аргумента извлекаются и отформатированы.

`FIF_ARGS_ALL`\
Извлекать и форматировать тип, имя и значение всех аргументов.

`FIF_ARGS_NOFORMAT`\
Указывается, что аргументы не отформатированы (например, не добавляйте всплывающие и закрывающие скобки вокруг списка аргументов и не добавляйте сепаратор между аргументами).

`FIF_ARGS_NO_FUNC_EVAL`\
Упцирование оценки функции (свойства) не следует использовать при извлечении значений аргумента.

`FIF_FILTER_NON_USER_CODE`\
Движок отладки предназначен для фильтрации непользовательских кадров кода, чтобы они не были включены.

`FIF_ARGS_NO_TOSTRING`\
Не разрешают оценку `ToString()` функции или форматирование при возврате аргументов функции.

`FIF_DESIGN_TIME_EXPR_EVAL`\
Информация о кадрах должна быть получена из размещенного домена приложения, а не из процесса хостинга.

## <a name="remarks"></a>Примечания
Эти флаги передаются методам [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) и [GetInfo,](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) чтобы указать, какие поля должны быть инициализированы в структуре или структурах [FRAMEINFO.](../../../extensibility/debugger/reference/frameinfo.md)

Эти флаги также используются для указания того, какие поля структуры [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) используются и действительны при возврате структуры. Эти значения могут быть объединены `OR`с bitwise .

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
