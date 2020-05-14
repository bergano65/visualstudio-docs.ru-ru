---
title: IDebugParsedВыражение (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22069b8eedb06d67eafaf7333f379a057c1b6f23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725994"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Этот интерфейс представляет собой разогнанные выражения, готовые к оценке.

## <a name="syntax"></a>Синтаксис

```
IDebugParsedExpression : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Оценщик выражения реализует этот интерфейс, чтобы представить разогнанные выражения, которые готовы к оценке.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Звонок [в Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) возвращает этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице `IDebugParsedExpression`показан метод .

|Метод|Описание|
|------------|-----------------|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Оценивает разогнанный выражение.|

## <a name="remarks"></a>Примечания
 Когда абонент готов оценить выражение, он вызывает [EvaluateSync,](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) чтобы вернуть [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) содержащий результат оценки. Этот двухэтапный подход к оценке, разбор, а затем оценка, позволяет разогнанные выражения для оценки несколько раз, в обход трудоемкий процесс разбора выражения.

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Синтаксический анализ](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
