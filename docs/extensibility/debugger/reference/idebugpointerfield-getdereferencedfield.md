---
title: IDebugPointerField::GetDereferencedField | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fef8ee4e584703338afd09e5303ac184f28b3a49
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331614"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Этот метод возвращает тип объекта, на который указывает этот указатель на объект.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Параметры
`ppField`\
[out] Возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) описанием типа целевого объекта.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Например, если [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) объекта указывает на целое, [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) тип, возвращаемый этим методом описывает типа integer.

## <a name="see-also"></a>См. также
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)