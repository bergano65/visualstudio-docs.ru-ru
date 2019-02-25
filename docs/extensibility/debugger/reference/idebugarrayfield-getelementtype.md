---
title: IDebugArrayField::GetElementType | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd80c54d436698e14db69bb356bd0cca61aa6ea3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682366"
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
Получает тип элемента в массиве.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetElementType( 
   IDebugField** ppType
);
```

```csharp
int GetElementType(
   out IDebugField ppType
);
```

#### <a name="parameters"></a>Параметры
 `ppType`

 [out] Возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , описывающий тип элемента.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) объект предполагает, что все элементы массива относятся к одному типу.

## <a name="see-also"></a>См. также
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)