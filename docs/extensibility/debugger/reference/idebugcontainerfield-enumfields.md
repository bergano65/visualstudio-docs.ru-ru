---
title: IDebugContainerfield::EnumFields Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afc461d52f81afc2c2e7127a90313bea7b9dacf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733223"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Создает регистратор для полей контейнера.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumFields( 
   FIELD_KIND         dwKindFilter,
   FIELD_MODIFIERS    dwModifiersFilter,
   LPCOLESTR          pszNameFilter,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumFields(
   enum_ FIELD_KIND      dwKindFilter,
   enum_ FIELD_MODIFIERS dwModifiersFilter,
   string                pszNameFilter,
   NAME_MATCH            nameMatch,
   out IEnumDebugFields  ppEnum
);
```

## <a name="parameters"></a>Параметры
`dwKindFilter`\
(в) Сочетание [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) констант, которые выбирают поля для перечисления. Виды полей могут описывать типы хранилищ, такие как класс или примитивная, или конкретную информацию, например локальную, параметрную или "эту" указку.

`dwModifiersFilter`\
(в) Комбинация [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) констант, которые выбирают перечисленные поля. Полевыми модификаторами могут быть разрешения доступа, такие как общедоступные или частные, или сведения о хранении, такие как виртуальные, статические или окончательные.

`pszNameFilter`\
(в) Название поля, которое будет перечислено. Это может быть нулевая величина, если все поля должны быть возвращены.

`nameMatch`\
(в) Значение из [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) перечисления, которое контролирует, является ли поиск чувствительным или нет.

`ppEnum`\
(ваут) Возвращает объект [IEnumDebugFields,](../../../extensibility/debugger/reference/ienumdebugfields.md) представляющий список полей. Возвращает нулевую стоимость, если нет полей.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращает S_OK или S_FALSE, если нет полей. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 В `dwKindFilter` `dwModifiersFilter`, `pszNameFilter` и параметры могут быть объединены, например, для выбора всех публичных виртуальных методов под названием "MyMethod".

## <a name="see-also"></a>См. также
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
