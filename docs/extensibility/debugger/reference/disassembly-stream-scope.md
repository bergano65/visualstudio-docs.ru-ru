---
title: DISASSEMBLY_STREAM_SCOPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 446b0eec7593457ed2cd384eb9a6bca383094e62
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684498"
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
Задает область потока Дизассемблированный код.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
typedef DWORD DISASSEMBLY_STREAM_SCOPE;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
```

## <a name="members"></a>Участники
DSS_HUGE указывает, что Дизассемблирование контекст кода создаст несколько выходных данных, чем клиент обычно необходимо получить в одном вызове.

Должен быть дизассемблирован DSS_FUNCTION указывает, что функция содержится в контексте кода. Указывает, что поток Дизассемблированный код представляет функцию, при возврате [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) метод.

Возвращенный DSS_MODULE при `IDebugDisassemblyStream2::GetScope` методом, указывает, что поток Дизассемблированный код представляет модуль.

Указывает DSS_ALL Дизассемблированный код для во всем адресном пространстве.

## <a name="remarks"></a>Примечания
Передается в качестве аргумента для [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) метод и возвращенный [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) метод.

Эти значения могут объединяться с побитовым объектом `OR`.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
