---
title: IDebugContainerField::EnumFields | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 368b076f592cff44e95e7156265c049a143fe1a3
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205816"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Создает перечислитель для полей контейнера.

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
[in] Сочетание [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) константы, выберите поля, которые необходимо перечислить. Типы полей можно описать типы хранилища, например класса или примитивных или определенные сведения, такие как local, параметра или указатель «this».

`dwModifiersFilter`\
[in] Сочетание [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) константы, выберите поля, которые необходимо перечислить. Модификаторы поля могут быть разрешения на доступ, такие как public, private или хранения сведения, такие как виртуальные, статическими или окончательными.

`pszNameFilter`\
[in] Имя поля, которые необходимо перечислить. Это может быть значение null, если все поля должны быть возвращены.

`nameMatch`\
[in] Значение из [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) перечисление, управляет ли поиск с учетом регистра, или нет.

`ppEnum`\
[out] Возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список полей. Возвращает значение null, если нет полей.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK или S_FALSE, если нет полей. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 `dwKindFilter`, `dwModifiersFilter`, И `pszNameFilter` параметры можно объединить, например, чтобы выбрать все публичные виртуальные методы, с именем «MyMethod».

## <a name="see-also"></a>См. также
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)