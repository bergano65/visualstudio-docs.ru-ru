---
title: IDebugPointerField::GetDereferencedField | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51ddd954e069ae2f6a683b727305808b8591d4f2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872047"
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

#### <a name="parameters"></a>Параметры
 `ppField`

 [out] Возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) описанием типа целевого объекта.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Например, если [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) объекта указывает на целое, [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) тип, возвращаемый этим методом описывает типа integer.

## <a name="see-also"></a>См. также
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)