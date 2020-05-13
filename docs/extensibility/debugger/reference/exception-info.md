---
title: EXCEPTION_INFO Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a305d34123d02b1fdbd545a438db4461643ed185
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737028"
---
# <a name="exception_info"></a>EXCEPTION_INFO
Описывает исключение или ошибку времени выполнения, брошенную отладкой программы.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagEXCEPTION_INFO {
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    BSTR            bstrExceptionName;
    DWORD           dwCode;
    EXCEPTION_STATE dwState;
    GUID            guidType;
} EXCEPTION_INFO;
```

```csharp
public struct EXCEPTION_INFO {
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public string         bstrExceptionName;
    public uint           dwCode;
    public uint           dwState;
    public Guid           guidType;
};
```

## <a name="members"></a>Участники
`pProgram`\
Объект [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) представляющий программу, в которой произошло исключение.

`bstrProgramName`\
Название программы, в которой произошло исключение.

`bstrExceptionName`\
Имя исключения.

`dwCode`\
Идентификационный код для исключения или ошибки времени выполнения.

`dwState`\
Значение из [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) перечисления, определяющее состояние исключения.

`guidType`\
Идентификатор языка `guidLang` GUID, или `guidEng`.

## <a name="remarks"></a>Примечания
Эта структура передается в качестве параметра методам [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) и [RemoveSetException.](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) Эта структура также передается методу [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) для заполнения.

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
- [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
