---
title: IDebugExpressionEvaluator::Parse | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5a93d909fbc8882c5864097a2a36c36749327a2d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62843138"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Этот метод преобразует строку выражения проанализированное выражение.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Parse( 
   LPCOLESTR                upstrExpression,
   PARSEFLAGS               dwFlags,
   UINT                     nRadix,
   BSTR*                    pbstrError,
   UINT*                    pichError,
   IDebugParsedExpression** ppParsedExpression
);
```

```csharp
int Parse(
   string                     upstrExpression,
   enum_PARSEFLAGS            dwFlags,
   uint                       nRadix,
   out string                 pbstrError,
   out uint                   pichError,
   out IDebugParsedExpression ppParsedExpression
);
```

#### <a name="parameters"></a>Параметры
 `upstrExpression`

 [in] Строка выражения, который необходимо проанализировать.

 `dwFlags`

 [in] Коллекция [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) константы, которые определяют, как выражение для синтаксического анализа.

 `nRadix`

 [in] Основание системы счисления для использования для интерпретации все числовые данные.

 `pbstrError`

 [out] Возвращает ошибку в виде удобочитаемого текста.

 `pichError`

 [out] Возвращает позицию символа начинается ошибка в строке выражения.

 `ppParsedExpression`

 [out] Возвращает проанализированное выражение в [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) объекта.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод создает проанализированное выражение, а не фактического значения. Проанализированное выражение готов для вычисления, то есть преобразовать в значение.

## <a name="see-also"></a>См. также
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)