---
title: IDebugProperty2::EnumChildren Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6d3908c469b489eb16e4662f7515ea624825e3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721512"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Извлекает список дочерних детей отеля.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumChildren ( 
   DEBUGPROP_INFO_FLAGS      dwFields,
   DWORD                     dwRadix,
   REFGUID                   guidFilter,
   DBG_ATTRIB_FLAGS          dwAttribFilter,
   LPCOLESTR                 pszNameFilter,
   DWORD                     dwTimeout,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFields,
   uint                        dwRadix,
   ref Guid                    guidFilter,
   uint                        dwAttribFilter,
   string                      pszNameFilter,
   uint                        dwTimeout,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Параметры
`dwFields`\
(в) Сочетание флагов [из DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) перечисления, которое определяет, какие поля в перечисленных [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры должны быть заполнены.

`dwRadix`\
(в) Определяет сятик, который будет использоваться при форматировании любой численной информации.

`guidFilter`\
(в) GUID фильтра, используемого с `dwAttribFilter` `pszNameFilter` параметрами для выбора, какие `DEBUG_PROPERTY_INFO` дети должны быть перечислены. Например, `guidFilterLocals` фильтры для локальных переменных.

`dwAttribFilter`\
(в) Комбинация флагов из [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) перечисления, которая определяет, какой тип объектов `DBG_ATTRIB_METHOD` перечислить, например для всех методов, которые могут быть детьми этого свойства. Используется в `guidFilter` сочетании `pszNameFilter` с параметрами.

`pszNameFilter`\
(в) Название фильтра, используемого `guidFilter` `dwAttribFilter` с параметрами `DEBUG_PROPERTY_INFO` для выбора, какие дети должны быть перечислены. Например, установка этого параметра на фильтры "MyX" для всех детей с названием "MyX".

`dwTimeout`\
(в) Определяет максимальное время, в миллисекундах, чтобы ждать, прежде чем вернуться из этого метода. Используйте, `INFINITE` чтобы ждать бесконечно.

`ppEnum`\
(ваут) Возвращает объект [IEnumDebugPropertyInfo2,](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) содержащий список свойств ребенка.

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
