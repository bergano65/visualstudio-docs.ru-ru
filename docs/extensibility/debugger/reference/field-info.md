---
title: FIELD_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 352e4bdf6c79dc67f0bf396cb1164e96e80fbf5f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337703"
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
`dwFields`\
Сочетание флагов из [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) перечисление, указывающее, какие члены будут заполнены.

`bstrFullName`\
Полное имя поля.

`bstrName`\
Короткое имя поля.

`bstrType`\
Тип поля.

`dwModifiers`\
Сочетание флагов из [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) перечисление, описывающее поле.

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
