---
title: IDebugArrayObject::GetElement | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 527302a2e6d6fc2884107e3773402adc56b881c7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322221"
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
[in] Индекс элемента.

`ppElement`\
[out] Возвращает [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейс, представляющий элемент.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод видит все элементы объекта массива как одномерный массив, даже если объект массива имеет несколько измерений. Например, если имеется массив `myarray[3][2][6]` и `dwIndex` параметр 20, этот метод возвращает элемент из `myarray[1][1][2]`и `dwIndex` параметр 21 вернет элемент из `myarray[1][1][3]`. Используйте [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) метод, чтобы определить общее число элементов в массиве.

## <a name="see-also"></a>См. также
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)