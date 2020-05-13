---
title: Интерфейсы оценки экспрессии Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da230a2da87b2dd3e3a85ce3ec6c914e829ccc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736939"
---
# <a name="expression-evaluation-interfaces"></a>Интерфейсы вычисления выражений
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Ниже приведены интерфейсы оценки [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] экспрессии для Debugging SDK.

## <a name="discussion"></a>Обсуждение
 Эти интерфейсы используются для оценки выражений в стеке вызовов во время перерыва. Они реализуются только для общих языковых оценщиков экспрессии (EE).

 Каждый интерфейс в таблице показывает компонент, который может реализовать его из следующего списка:

- Двигатель дебуга (DE)

- Оценка экспрессии (EE)

- Визуальная студия (VS)

|Интерфейс|Реализовано|Описание|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Представляет числовый псевдоним для переменной.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Представляет собой числовый псевдоним для переменной и позволяет оценщику выражения (EE) получить домен приложения для псевдонима.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Представляет объект массива.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Представляет объект управляемого массива и позволяет оценщику выражения (EE) определить базовый индекс (нижние границы) для массива.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Представляет связующего, связывающего символы отладки с фактическими адресами в памяти.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|То же, что и интерфейс [IDebugBinder,](../../../extensibility/debugger/reference/idebugbinder.md) но предоставляет доступ к типам, псевдонимам и пользовательским визуализаторам.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Представляет средство оценки выражений.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Представляет собой расширенную версию оценщика выражения (EE).|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Представляет оценщика выражения (EE) с расширенным деревом парзера.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Представляет функцию.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Представляет функцию и улучшает интерфейс [IDebugFunction.](../../../extensibility/debugger/reference/idebugfunctionobject.md)|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Позволяет оценщику выражения (EE) отображать сообщение в окне вывода отладчика.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Представляет управляемый объект кода.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Базовый интерфейс, представляющий любой символ, связанный с адресом памяти.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|То же, что и интерфейс [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) но предоставляет доступ к дополнительной информации.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Представляет собой разогнанные выражения, готовые к оценке.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Представляет указатель.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Представляет указатель в дереве разбора и расширяет интерфейс **IDebugPointerObject.**|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Обеспечивает возможность изменения значения типа с помощью визуализатора типа.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Предоставляет доступ к пользовательским зрителям и ввизуализаторам.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Предоставляет возможность создания объекта [IEEVisualizerService.](../../../extensibility/debugger/reference/ieevisualizerservice.md)|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Представляет коллекцию объектов [IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md)|

## <a name="see-also"></a>См. также
- [Справка по API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Запись вычислителя выражений CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
