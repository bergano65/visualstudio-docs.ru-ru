---
title: CONTEXT_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6c50d5ea930f05d22b68416978909cceca17727d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346467"
---
# <a name="contextinfo"></a>CONTEXT_INFO
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
Сочетание флагов из он [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) перечисление, указывающее, какие поля заполняются<strong>.</strong>

`bstrModuleUrl`\
Имя модуля, где находится контекст.

`bstrFunction`\
Имя функции, где находится контекст.

`posFunctionOffset`\
Объект [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) структуру, которая определяет смещение строки и столбца функции, связанные с контекст кода.

`bstrAddress`\
Адрес в коде, где находится данный контекст.

`bstrAddressOffset`\
Смещение по адресу в коде, где находится данный контекст.

`bstrAddressAbsolute`\
Абсолютный адрес в памяти, где находится данный контекст.

## <a name="remarks"></a>Примечания
Эта структура возвращается из вызова [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) метод.

Обычно эта структура используется поддержки **памяти** окно отладки.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
