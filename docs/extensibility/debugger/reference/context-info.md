---
title: CONTEXT_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4838df34c14b936af15b8a7a582a6d30ea12bee1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737565"
---
# <a name="context_info"></a>CONTEXT_INFO
Эта структура описывает контекст памяти или контекст кода.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagCONTEXT_INFO {
    CONTEXT_INFO_FIELDS dwFields;
    BSTR                bstrModuleUrl;
    BSTR                bstrFunction;
    TEXT_POSITION       posFunctionOffset;
    BSTR                bstrAddress;
    BSTR                bstrAddressOffset;
    BSTR                bstrAddressAbsolute;
} CONTEXT_INFO;
```

```csharp
public struct CONTEXT_INFO {
    public uint          dwFields;
    public string        bstrModuleUrl;
    public string        bstrFunction;
    public TEXT_POSITION posFunctionOffset;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrAddressAbsolute;
};
```

## <a name="members"></a>Участники
`dwFields`\
Сочетание флагов из [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) перечисление, которое указывает, какие поля заполняются<strong>.</strong>

`bstrModuleUrl`\
Имя модуля, в котором находится контекст.

`bstrFunction`\
Имя функции, в которой находится контекст.

`posFunctionOffset`\
Структура [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , определяющая смещение строки и столбца функции, связанной с контекстом кода.

`bstrAddress`\
Адрес в коде, где находится заданный контекст.

`bstrAddressOffset`\
Смещение адреса в коде, где находится заданный контекст.

`bstrAddressAbsolute`\
Абсолютный адрес в памяти, где находится заданный контекст.

## <a name="remarks"></a>Remarks
Эта структура возвращается из вызова метода " [info](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) ".

Типичное использование этой структуры — поддержка окна отладки **памяти** .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
