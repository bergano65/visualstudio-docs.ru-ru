---
title: IDebugObject::IsEqual | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf592fa83a18c47bf676b84073c0be0e4cb476e8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323587"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Сравнивает объект с данным объектом.

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
[in] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , который представляет объект для сравнения.

`pfIsEqual`\
[out] Возвращает ненулевое значение (`TRUE`) Если значения объектов равны; в противном случае возвращает ноль (`FALSE`).

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Как правило, этот метод можно сравнить адреса значений, представленных `pObject` параметр и это [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объекта; Если адреса совпадают, то объекты могут быть рассматриваются как равные.

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)