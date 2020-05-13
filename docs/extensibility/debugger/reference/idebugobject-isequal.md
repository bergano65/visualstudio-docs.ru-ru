---
title: IDebugObject::Equal Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13018e31fb5f8bed89a0a290d687360a605a855d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726505"
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
(в) Объект [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) представляющий объект для сравнения.

`pfIsEqual`\
(ваут) Возвращает ненулевой`TRUE`( ), если значения объектов равны; в противном`FALSE`случае, возвращаетнулно ноль ().

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Как правило, этот метод может сравнить адреса значений, представленных `pObject` параметром, и этого объекта [IDebugObject;](../../../extensibility/debugger/reference/idebugobject.md) если адреса равны, то объекты могут считаться равными.

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
