---
title: DEBUG_REFERENCE_INFO Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e31205f52151679f932877c9c4fdc56907ea59e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737411"
---
# <a name="debug_reference_info"></a>DEBUG_REFERENCE_INFO
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
Комбинация флагов [из DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) перечисления, которая определяет, какие поля заполнены.

`bstrName`\
Указанное пользователем имя объекта [IDebugReference2.](../../../extensibility/debugger/reference/idebugreference2.md)

`bstrType`\
Тип отсчета как отформатированная строка.

`bstrValue`\
Справочное значение как отформатированная строка

`dwAttrib`\
Комбинация флагов из [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) перечисления, которая определяет флаги для атрибутов свойства отладки.

`dwRefType`\
Значение из [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) перечисления, которое определяет, является ли тип ссылки сильным или слабым.

`m_pReference`\
Объект [IDebugReference2,](../../../extensibility/debugger/reference/idebugreference2.md) который определяет справочную информацию.

## <a name="remarks"></a>Примечания
Эта структура передается на вызов к методу [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) для заполнения. Эта структура также возвращается как часть списка из интерфейса [IEnumDebugReferenceInfo2,](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) который, в свою очередь, возвращается из вызова в метод [EnumChildren.](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

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
