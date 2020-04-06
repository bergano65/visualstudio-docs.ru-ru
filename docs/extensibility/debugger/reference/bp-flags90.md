---
title: BP_FLAGS90 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5628af4a6e5c4deae3de02340e882bd2605e22d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738045"
---
# <a name="bp_flags90"></a>BP_FLAGS90
Перечисляет действительные значения для дополнительных флагов. Дополнительные флаги могут использоваться для указания дополнительной информации при установке точки разрыва. Этот пересчет расширяет [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) перечисление.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE               = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION    = 0x0001,
    BP90_FLAG_DONT_STOP          = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
typedef DWORD BP_FLAGS90;
```

```csharp
public enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE                = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION     = 0x0001,
    BP90_FLAG_DONT_STOP           = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
```

## <a name="fields"></a>Поля
`BP90_FLAG_NONE`\
Указывает отсутствие флага точки разрыва.

`BP90_FLAG_MAP_DOCPOSITION`\
Уточняется, что движок отладки (DE) должен отобразить точку разрыва с помощью позиции документа. Это применимо только к точкам разрыва, установленным в исходных файлах, ориентированных на сценарий, таких как Active Server Pages (ASP).

`BP90_FLAG_DONT_STOP`\
Уточняется, что точка разрыва должна быть обработана двигателем отладки, но что отладка двигателя в конечном счете, не должна останавливаться на достигнутом; то есть объект события [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) не должен отправляться. Этот флаг предназначен для использования в основном со следами.

`BP90_FLAG_TRACEPOINT_CONTINUE`\
Используется нативной отладкой двигателя, чтобы определить, следует ли очищать состояние шага. Он отличается от BP90_FLAG_DONT_STOP, поскольку BP90_FLAG_DONT_STOP не устанавливается, если точка трассировки выполняет макрос.

## <a name="requirements"></a>Требования
Заголовок: Msdbg90.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
