---
title: IDebugBinder::GetFunctionObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b69af018a1b5b1ddf743784f4736d7c2ac24d45f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712298"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Этот метод возвращает [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) объект, используемый для создания параметров функции.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetFunctionObject( 
   IDebugFunctionObject **ppFunction
);
```

```csharp
int GetFunctionObject(
   out IDebugFunctionObject ppFunction
);
```

#### <a name="parameters"></a>Параметры
 `ppFunction`

 [out] Возвращает [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) интерфейс, который используется для создания параметров функции.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)