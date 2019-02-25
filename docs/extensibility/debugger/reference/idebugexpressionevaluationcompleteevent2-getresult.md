---
title: IDebugExpressionEvaluationCompleteEvent2::GetResult | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cc3122103b075b18d2e77e72ad50cda958ba715
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678713"
---
# <a name="idebugexpressionevaluationcompleteevent2getresult"></a>IDebugExpressionEvaluationCompleteEvent2::GetResult
Возвращает результат вычисления выражения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetResult( 
   IDebugProperty2** ppResult
);
```

```csharp
int GetResult( 
   out IDebugProperty2 ppResult
);
```

#### <a name="parameters"></a>Параметры
 `ppResult`

 [out] Возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объект, представляющий результат вычисления выражения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Возвращенный [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объект содержит значение вычисленного выражения. Обратите внимание, что это значение может быть сложное значение, например массивы, но результат должен быть числовое или строковое значение, которое отображается для пользователя.

## <a name="see-also"></a>См. также
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)