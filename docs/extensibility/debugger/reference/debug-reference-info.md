---
title: DEBUG_REFERENCE_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c22ab1a7d0cb03f66455f76c1d9878a9df76604e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346135"
---
# <a name="debugreferenceinfo"></a>DEBUG_REFERENCE_INFO
Описывает ссылку.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagDEBUG_REFERENCE_INFO {
    DEBUGREF_INFO_FLAGS dwFields;
    BSTR                bstrName;
    BSTR                bstrType;
    BSTR                bstrValue;
    DBG_ATTRIB_FLAGS    dwAttrib;
    REFERENCE_TYPE.     dwRefType;
    IDebugReference2*   m_pReference;
} DEBUG_REFERENCE_INFO;
```

```csharp
public struct DEBUG_REFERENCE_INFO {
    public uint             dwFields;
    public string           bstrName;
    public string           bstrType;
    public string           bstrValue;
    public ulong            dwAttrib;
    public uint.            dwRefType;
    public IDebugReference2 m_pReference;
};
```

## <a name="members"></a>Участники
`dwFields`\
Сочетание флагов из [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) перечисление, указывающее, какие поля заполнены.

`bstrName`\
Определяемое пользователем имя [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) объекта.

`bstrType`\
Ссылочный тип, как отформатированную строку.

`bstrValue`\
Значение ссылки как отформатированную строку

`dwAttrib`\
Сочетание флагов из [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) перечисление, указывающее флаги для атрибутов свойства отладки.

`dwRefType`\
Значение из [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) перечисление, указывающее, является ли тип ссылки строгие или слабые.

`m_pReference`\
[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , указывающий справочные сведения.

## <a name="remarks"></a>Примечания
Эта структура передается в вызов [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) метод для заполнения. Эта структура также возвращается как часть списка из [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) интерфейс, который, в свою очередь, возвращается из вызова [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) метод.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
