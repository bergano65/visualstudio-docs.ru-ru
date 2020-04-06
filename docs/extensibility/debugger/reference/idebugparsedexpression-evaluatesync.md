---
title: IDebugParsedExpression::EvaluateSync Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f00b209ff5f91d160e89f5f55ad966fbe9e6414
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726007"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Этот метод оценивает разобранное выражение и дополнительно отбрасывает результат в другой тип данных.

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
(в) Сочетание констант [EVALFLAGS,](../../../extensibility/debugger/reference/evalflags.md) которые контролируют, как выражение должно быть оценено.

`dwTimeout`\
(в) Определяет максимальное время, в миллисекундах, чтобы ждать, прежде чем вернуться из этого метода. Используйте, `INFINITE` чтобы ждать бесконечно.

`pSymbolProvider`\
(в) Поставщик символов, выраженный как интерфейс [IDebugSymbolProvider.](../../../extensibility/debugger/reference/idebugsymbolprovider.md)

`pAddress`\
(в) Текущее местоположение выполнения в методе, выраженное как интерфейс [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

`pBinder`\
(в) Связующее звено, выраженное как интерфейс [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)

`bstrResultType`\
(в) Тип результата должен быть отлит. Этот аргумент может быть нулевая стоимость.

`ppResult`\
(ваут) Возвращает интерфейс [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) представляющий результаты оценки.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Контекст оценки выражения `pAddress`дается, что позволяет определить содержащий метод, а затем использовать правила языкового скопирования для определения значения символов в выражении.

## <a name="see-also"></a>См. также
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
