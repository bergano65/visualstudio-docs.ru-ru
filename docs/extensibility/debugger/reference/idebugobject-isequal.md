---
title: 'Идебугобжект:: Equals | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 406e93456f1bd6d92a42f1584d19aeb52dd5ff93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846781"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Сравнивает объект с этим объектом.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsEqual( 
   IDebugObject* pObject,
   BOOL*         pfIsEqual
);
```

```csharp
int IsEqual(
   IDebugObject pObject,
   out int      pfIsEqual
);
```

## <a name="parameters"></a>Параметры
`pObject`\
окне Объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий объект для сравнения.

`pfIsEqual`\
заполняет Возвращает ненулевое значение ( `TRUE` ), если значения объектов равны; в противном случае возвращает ноль ( `FALSE` ).

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Как правило, этот метод может сравнивать адреса значений, представленных `pObject` параметром, и этого объекта [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) . Если адреса равны, объекты можно считать равными.

## <a name="see-also"></a>См. также раздел
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
