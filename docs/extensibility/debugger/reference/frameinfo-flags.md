---
title: FRAMEINFO_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 54bb93fa6f88c02731691728bceacdd4a5fe2036
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694352"
---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
Указывает сведения для получения о кадр стека.

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

## <a name="members"></a>Участники
FIF_FUNCNAME Initialize и использование `m_bstrFuncName` поля.

FIF_RETURNTYPE Initialize и использование `m_bstrReturnType` поля.

FIF_ARGS Initialize и использование `m_bstrArgs` поля.

FIF_LANGUAGE Initialize и использование `m_bstrLanguage` поля.

FIF_MODULE Initialize и использование `m_bstrModule` поля.

FIF_STACKRANGE Initialize и использование `m_addrMin` и `m_addrMax` поля (stack диапазона).

FIF_FRAME Initialize и использование `m_pFrame` поля.

FIF_DEBUGINFO Initialize и использование `m_fHasDebugInfo` поля.

FIF_STALECODE Initialize и использование `m_fStaleCode` поля.

FIF_ANNOTATEDFRAME Initialize и использование `m_fAnnotatedFrame` поля.

FIF_DEBUG_MODULEP Initialize и использование `m_pModule` поля.

FIF_FUNCNAME_FORMAT форматирует имя функции. Результат возвращается в `m_bstrFunName` поля и другие поля не заполнены.

FIF_FUNCNAME_RETURNTYPE добавляет тип возвращаемого значения на `m_bstrFuncName` поля.

Аргументы, добавляет FIF_FUNCNAME_ARGS `m_bstrFuncName` поля.

Язык, который добавляет FIF_FUNCNAME_LANGUAGE `m_bstrFuncName` поля.

FIF_FUNCNAME_MODULE добавляет имя модуля для `m_bstrFuncName` поля.

FIF_FUNCNAME_LINES добавляет число строк, которые должны `m_bstrFuncName` поля.

Добавляет FIF_FUNCNAME_OFFSET `m_bstrFuncName` поле Смещение в байтах от начала строки, если `FIF_FUNCNAME_LINES` указан. Если `FIF_FUNCNAME_LINES` не указан, или если номера строк недоступны, добавляет смещение в байтах от начала функции.

FIF_FUNCNAME_ARGS_TYPES добавляет тип каждого аргумента для `m_bstrFuncName` поля.

FIF_FUNCNAME_ARGS_NAMES добавляет имя для каждого аргумента `m_bstrFuncName` поля.

FIF_FUNCNAME_ARGS_VALUES добавляет значение каждого аргумента для `m_bstrFuncName` поля.

FIF_FUNCNAME_ARGS_ALL добавляет тип, имя и значение всех аргументов `m_bstrFuncName` поля.

FIF_ARGS_TYPES извлекаются и отформатирован типов аргументов.

FIF_ARGS_NAMES извлекаются имена аргументов и формат.

FIF_ARGS_VALUES значения аргументов извлекаются и отформатирован.

Получить FIF_ARGS_ALL и формат типа, имя и значение всех аргументов.

FIF_ARGS_NOFORMAT указывает, что аргументы имеют формат (например, не Добавьте открывающую и закрывающую скобки вокруг списка аргументов и не добавлять разделитель между аргументами).

FIF_ARGS_NO_FUNC_EVAL указывает, что вычисление (свойство) функции не следует при извлечении значения аргументов.

FIF_FILTER_NON_USER_CODE модуль отладки — отфильтровать кадры не написанный пользователем код, чтобы они не включаются.

FIF_ARGS_NO_TOSTRING не допускают `ToString()` функции оценки или форматирования при возврате аргументы функции.

Сведения о кадре FIF_DESIGN_TIME_EXPR_EVAL следует получить из размещенного домена приложения, а не процесс размещения.

## <a name="remarks"></a>Примечания
Эти флаги передаются [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) и [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) методы, чтобы указать, какие поля должны быть инициализированы в [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структурой или структурами.

Эти флаги также используются для указания поля [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры не используются и допустимым при возвращении структуры. Эти значения могут объединяться с побитовым объектом `OR`.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
