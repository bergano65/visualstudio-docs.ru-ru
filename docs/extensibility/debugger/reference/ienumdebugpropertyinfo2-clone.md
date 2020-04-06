---
title: IEnumDebugPropertyInfo2:Клон Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::Clone
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Clone
ms.assetid: 0ede1667-1071-4aa4-b887-260ea103d724
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c98917de4bcdc7bf5ff184591b42133626a4f16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715563"
---
# <a name="ienumdebugpropertyinfo2clone"></a>IEnumDebugPropertyInfo2::Clone
Возвращает копию текущего перечисления как отдельный объект.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Clone(
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
[out] Возвращает копию этого перечисления как отдельный объект.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Копия перечисления имеет то же состояние, что и исходное состояние на момент вызова этого метода. Тем не менее, состояния копии и оригинала являются отдельными и могут быть изменены по отдельности.

## <a name="see-also"></a>См. также
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
