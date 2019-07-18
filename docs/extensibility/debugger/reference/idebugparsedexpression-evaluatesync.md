---
title: IDebugParsedExpression::EvaluateSync | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aac58831224a6bebadd625dad72177f2aec3fc76
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311826"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Этот метод вычисляет проанализированное выражение и при необходимости приводит результат к другому типу данных.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EvaluateSync( 
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BSTR                  bstrResultType,
   IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   string               bstrResultType,
   out IDebugProperty2  ppResult
);
```

## <a name="parameters"></a>Параметры
`dwEvalFlags`\
[in] Сочетание [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) константы, определяющие, каким образом будет вычисляться выражение.

`dwTimeout`\
[in] Указывает максимальное время в миллисекундах для ожидания перед возвратом из этого метода. Используйте `INFINITE` для неограниченного времени ожидания.

`pSymbolProvider`\
[in] Поставщик символов, выраженное как [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) интерфейс.

`pAddress`\
[in] Текущее положение выполнения внутри метода, выраженное как [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс.

`pBinder`\
[in] Связыватель, выраженное как [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) интерфейс.

`bstrResultType`\
[in] Тип результата должен быть приведен к. Этот аргумент может принимать значение null.

`ppResult`\
[out] Возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) интерфейс, представляющий результаты оценки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Контекст вычисления выражений определяется формулой `pAddress`, который дает возможность определить, содержащего метода и области использования языка правил для определения значения символов в выражении.

## <a name="see-also"></a>См. также
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)