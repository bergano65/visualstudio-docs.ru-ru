---
title: IDebugExpressionEvaluator::SetLocale | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 730a105b12016ea031bdb4753da009223a5d39f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62540528"
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
Этот метод задает язык, используемый для создания печатного результатов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale(
   ushort wLangID
);
```

#### <a name="parameters"></a>Параметры
 `wLangID`

 [in] Идентификатор языка.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод может вызываться многократно хотя средство оценки выражений (EE) загружается, поэтому EE должен иметь возможность переключения языков в режиме реального времени. EE использует этот языковой стандарт для возврата сообщения об ошибках и строки на соответствующем языке.

## <a name="see-also"></a>См. также
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)