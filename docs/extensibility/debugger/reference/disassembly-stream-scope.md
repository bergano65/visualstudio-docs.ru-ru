---
title: DISASSEMBLY_STREAM_SCOPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 724e32f83cfec31c2bacdab661407983af87efe6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318246"
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

## <a name="fields"></a>Поля
`DSS_HUGE`\
Указывает, что Дизассемблирование контекст кода будет создавать дополнительные выходные данные, чем клиент обычно необходимо получить в одном вызове.

`DSS_FUNCTION`\
Указывает, что функции, содержащиеся в контексте кода должны быть дизассемблирован. Указывает, что поток Дизассемблированный код представляет функцию, при возврате [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) метод.

`DSS_MODULE`\
При возврате `IDebugDisassemblyStream2::GetScope` методом, указывает, что поток Дизассемблированный код представляет модуль.

`DSS_ALL`\
Указывает Дизассемблированный код для во всем адресном пространстве.

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
