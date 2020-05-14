---
title: IDebugArrayObject::GetElement Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e29fe09905119057224b45b455e4f56e5ce904af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736181"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Получает элемент массива.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetElement( 
   DWORD          dwIndex,
   IDebugObject** ppElement
);
```

```csharp
int GetElement(
   [In] uint dwIndex,
   out IDebugObject ppElement
);
```

## <a name="parameters"></a>Параметры
`dwIndex`\
(в) Индекс элемента.

`ppElement`\
(ваут) Возвращает интерфейс [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) представляющий элемент.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод рассматривает все элементы объекта массива как одномерный массив, даже если объект массива многомерный. Например, учитывая `myarray[3][2][6]` массив `dwIndex` и параметр 20, этот `myarray[1][1][2]`метод будет `dwIndex` возвращать элемент из, и `myarray[1][1][3]`параметр 21 будет возвращать элемент из . Используйте метод [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) для определения общего количества элементов в массиве.

## <a name="see-also"></a>См. также
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
