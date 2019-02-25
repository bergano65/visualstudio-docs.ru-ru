---
title: BP_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe346d708110cf16b85e84d61aeb25ee335c0e96
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688437"
---
# <a name="bpflags"></a>BP_FLAGS
Предоставляет необязательные флаги, которые могут использоваться для указания дополнительных сведений при задании точки останова.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
typedef DWORD BP_FLAGS;
```

```csharp
public enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
```

## <a name="members"></a>Участники
BP_FLAG_NONE указывает нет флага точки останова.

BP_FLAG_MAP_DOCPOSITION указывает, что модуль отладки (DE) должны сопоставляться с помощью документа положение точки останова. Это значение применимо только к точки останова в скрипт ориентированного исходных файлов таких как Active Server Pages (ASP).

BP_FLAG_DONT_STOP указывает, точки останова, которые должны обрабатываться с помощью обработчика отладки, но, отладчик в конечном счете следует не остановить существует (то есть [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) не следует отправлять объект события). Этот флаг предназначен для использования главным образом с использованием точек трассировки.

## <a name="remarks"></a>Примечания
Используется для `dwFlags` членом [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры.

Эти значения могут объединяться с побитовым объектом `OR`.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
