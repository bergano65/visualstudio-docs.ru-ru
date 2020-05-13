---
title: Интерфейсы оценки ключевых выражений (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01527edac4000f0b2f7b89fdd507fc093f0d7734
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738487"
---
# <a name="key-expression-evaluator-interfaces"></a>Интерфейсы оценщика ключевых выражений
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [оценщиками экспресс-оценщиков CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [выборкой управляемого оценщика](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)экспрессий.

 При написании оценщика выражения (EE), наряду с контекстом оценки, вы должны быть знакомы со следующими интерфейсами.

## <a name="interface-descriptions"></a>Описания интерфейса

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Имеет один метод, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), который получает структуру данных, которая представляет текущую точку выполнения. Эта структура данных является одним из трех аргументов, которые движок отладки (DE) переходит к методу [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) для оценки выражения. Этот интерфейс обычно реализуется поставщиком символов.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Имеет метод [Bind,](../../extensibility/debugger/reference/idebugbinder-bind.md) который получает область памяти, содержащую текущее значение символа. Учитывая как содержащий метод, представленный объектом [IDebugObject,](../../extensibility/debugger/reference/idebugobject.md) так и сам символ, `IDebugBinder::Bind` представленный объектом [IDebugField,](../../extensibility/debugger/reference/idebugfield.md) возвращает значение символа. `IDebugBinder`как правило, реализуется DE.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Представляет собой простой тип данных. Для более сложных типов, таких как массивы и методы, используйте полученные интерфейсы [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) и [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) соответственно. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) является еще одним важным производным интерфейсом, который представляет символы, содержащие другие символы, такие как методы или классы. Интерфейс `IDebugField` (и его производные) обычно реализуется поставщиком символов.

     Объект `IDebugField` может быть использован для поиска имени и типа символа и, вместе с объектом [IDebugBinder,](../../extensibility/debugger/reference/idebugbinder.md) может быть использован для поиска его значения.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Представляет фактические биты значения времени выполнения символа. [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) принимает объект [IDebugField,](../../extensibility/debugger/reference/idebugfield.md) который представляет символ, и возвращает объект [IDebugObject.](../../extensibility/debugger/reference/idebugobject.md) Метод [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) возвращает значение символа в буфер памяти. DE обычно реализует этот интерфейс для представления значения свойства в памяти.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Этот интерфейс представляет собой сам оценщик выражения. Ключевым методом является [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), который возвращает интерфейс [IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Этот интерфейс представляет собой разогнанные выражения, готовые к оценке. Ключевым методом является [EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) который возвращает IDebugProperty2, представляющий значение и тип выражения.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Этот интерфейс представляет ценность и его тип и является результатом оценки выражения.

## <a name="see-also"></a>См. также
- [Контекст оценки](../../extensibility/debugger/evaluation-context.md)
