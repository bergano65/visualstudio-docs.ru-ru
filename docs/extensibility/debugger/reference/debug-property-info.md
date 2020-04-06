---
title: DEBUG_PROPERTY_INFO Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34fc1b5103949a767a3ee448618cbb708ea6a48b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737445"
---
# <a name="debug_property_info"></a>DEBUG_PROPERTY_INFO
Содержит информацию об отладке свойства.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagDEBUG_PROPERTY_INFO {
    DEBUGPROP_INFO_FLAGS dwValidFields;
    BSTR                 bstrFullName;
    BSTR                 bstrName;
    BSTR                 bstrType;
    BSTR                 bstrValue;
    IDebugProperty2*     pProperty;
    DBG_ATTRIB_FLAGS     dwAttrib;
} DEBUG_PROPERTY_INFO;
```

```csharp
public struct DEBUG_PROPERTY_INFO {
    public uint            dwValidFields;
    public string          bstrFullName;
    public string          bstrName;
    public string          bstrType;
    public string          bstrValue;
    public IDebugProperty2 pProperty;
    public ulong           dwAttrib;
};
```

## <a name="members"></a>Участники
`dwValidFields`\
Комбинация флагов [из DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) перечисления, которая определяет, какие поля заполнены.

`bstrFullName`\
Полное название отеля.

`bstrName`\
Имя свойства в контексте.

`bstrType`\
Тип свойства как отформатированная строка.

`bstrValue`\
Значение свойства как отформатированная строка.

`pProperty`\
[Объект IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) описанный этой структурой.

`dwAttrib`\
Комбинация флагов из [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) перечисления, описывающая атрибуты этого свойства.

## <a name="remarks"></a>Примечания
Свойство — это объект иерархического характера, имевавкоторый имя, тип и ценность. Например, свойство может описывать локальные переменные, параметры, смотреть переменные и выражения, а также регистры.

Эта структура передается методу [GetPropertyInfo,](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) где она заполняется. Эта структура также возвращается как часть списка этой структуры из интерфейса [IEnumDebugPropertyInfo2,](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) который, в свою очередь, возвращается из вызова к методам [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) и [EnumProperties.](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
