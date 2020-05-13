---
title: CONTEXT_INFO Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
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
Сочетание флагов от него [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) перечисления, которая определяет, какие поля заполнены<strong>.</strong>

`bstrModuleUrl`\
Название модуля, в котором находится контекст.

`bstrFunction`\
Имя функции, в котором находится контекст.

`posFunctionOffset`\
Структура [TEXT_POSITION,](../../../extensibility/debugger/reference/text-position.md) которая определяет линию и столбец, смещение функции, связанной с контекстом кода.

`bstrAddress`\
Адрес в коде, где находится данный контекст.

`bstrAddressOffset`\
Смещение адреса в коде, в котором находится данный контекст.

`bstrAddressAbsolute`\
Абсолютный адрес в памяти, где находится данный контекст.

## <a name="remarks"></a>Примечания
Эта структура возвращается из вызова в метод [GetInfo.](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)

Типичное использование этой структуры в поддержку окна отладки **памяти.**

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
