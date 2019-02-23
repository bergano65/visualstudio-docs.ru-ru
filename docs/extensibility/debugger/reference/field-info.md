---
title: FIELD_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83cdacae192ad1286203139432a0eacd632b8511
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694235"
---
# <a name="fieldinfo"></a>FIELD_INFO
Локальная переменная, параметр или другому полю, описанном структурой.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagFieldInfo {
    FIELD_INFO_FIELDS dwFields;
    BSTR              bstrFullName;
    BSTR              bstrName;
    BSTR              bstrType;
    FIELD_MODIFIERS   dwModifiers;
} FIELD_INFO;
```

```csharp
public struct FIELD_INFO {
    public uint   dwFields;
    public string bstrFullName;
    public string bstrName;
    public string bstrType;
    public uint   dwModifiers;
};
```

## <a name="members"></a>Участники
dwFields объект сочетание флагов из [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) перечисление, указывающее, какие члены будут заполнены.

bstrFullName полное имя поля.

bstrName короткое имя поля.

bstrType тип поля.

dwModifiers объект сочетание флагов из [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) перечисление, описывающее поле.

## <a name="remarks"></a>Примечания
Эта структура передается [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) метод, где он заполняется.

## <a name="requirements"></a>Требования
Заголовок: sh.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
