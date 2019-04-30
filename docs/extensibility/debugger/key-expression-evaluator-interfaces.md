---
title: Основные интерфейсы вычислителя выражений | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 72407753960b38fc604d069d4e78b91a02eb737b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411206"
---
# <a name="key-expression-evaluator-interfaces"></a>Интерфейсы вычислителя ключевых выражений
> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образец средства оценки выражений управляемый](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 При составлении вычислителя выражений (EE), а также в контекст оценки, вы должны быть знакомы с следующие интерфейсы.

## <a name="interface-descriptions"></a>Описание интерфейса

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Единственный метод, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), который возвращает структуру данных, который представляет текущей точки выполнения. Эта структура данных является одним из трех аргументов, которые модуль отладки (DE) передает [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) метод для вычисления выражения. Этот интерфейс обычно реализуется поставщиком символ.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Имеет [привязать](../../extensibility/debugger/reference/idebugbinder-bind.md) метод, который получает область памяти, которая содержит текущее значение символа. Учитывая обоих содержащего метода, представленного [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) объект и самого символа, представленного [IDebugField](../../extensibility/debugger/reference/idebugfield.md) объекта, `IDebugBinder::Bind` возвращает значение символа. `IDebugBinder` обычно реализуют DE.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Представляет простой тип данных. Для более сложных типов, таких как массивы и методы, используйте производные [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) и [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) интерфейсы, соответственно. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) — другой важной производный интерфейс, представляющий символов, содержащий других символов, таких как методы и классы. `IDebugField` Интерфейс (и его производные) обычно реализуют поставщик символов.

     `IDebugField` Объект может быть используется, чтобы найти имя и тип символа и, вместе с [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) объекта, можно использовать для поиска его значения.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Представляет реальные биты значения времени выполнения символа. [Привязать](../../extensibility/debugger/reference/idebugbinder-bind.md) принимает [IDebugField](../../extensibility/debugger/reference/idebugfield.md) объект, который представляет символ и возвращает [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) объекта. [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) метод возвращает значение символа в буфере памяти. DE обычно реализует этот интерфейс для представления значения свойства в памяти.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Этот интерфейс представляет средство оценки выражений, сам. Ключевым методом является [проанализировать](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), который возвращает [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) интерфейс.

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Этот интерфейс представляет проанализированное выражение, готовое к вычислению. Ключевым методом является [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) который возвращает значение IDebugProperty2, предоставляющий значение и тип выражения.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Этот интерфейс, представляющий значение и его тип и является результатом вычисления выражения.

## <a name="see-also"></a>См. также
- [Контекст оценки](../../extensibility/debugger/evaluation-context.md)