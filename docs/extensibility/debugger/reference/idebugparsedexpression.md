---
title: IDebugParsedExpression | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5549b2c86df77907fd92bc2948deaa36fdceb353
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703426"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Этот интерфейс представляет проанализированное выражение, готовое к вычислению.

## <a name="syntax"></a>Синтаксис

```
IDebugParsedExpression : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Вычислитель выражений реализует этот интерфейс, представляющий проанализированное выражение, которая готова для оценки.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызов [проанализировать](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) возвращает этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны метод `IDebugParsedExpression`.

|Метод|Описание:|
|------------|-----------------|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Вычисляет проанализированное выражение.|

## <a name="remarks"></a>Примечания
 Когда вызывающий объект готов для вычисления выражения, он вызывает [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) для возврата [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , содержащее результат вычисления. Этот подход двух частей, для оценки, синтаксический анализ для последующего вычисления, проанализированное выражение, вычисляемое несколько раз, с обходом много времени процесс синтаксическом анализе выражения.

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Анализ](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)