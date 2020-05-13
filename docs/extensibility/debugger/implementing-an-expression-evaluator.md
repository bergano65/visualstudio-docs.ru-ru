---
title: Внедрение оценщика экспрессии Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8c7c9a1130794dd4c28f212afd6cb3c030f5a1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738537"
---
# <a name="implement-an-expression-evaluator"></a>Реализация оценщика выражения
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)CLR [см.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

 Оценка выражения представляет собой сложное взаимодействие между движком отладки (DE), поставщиком символов (SP), объектом связующего и оценщиком выражения (EE). Эти четыре компонента соединены интерфейсами, которые реализуются одним компонентом и потребляются другим.

 EE принимает выражение от DE в виде строки и разбирает или оценивает его. EE запускает следующие интерфейсы, которые потребляются DE:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  EE вызывает объект связующего, поставляемый DE, чтобы получить значение символов и объектов. EE потребляет следующие интерфейсы, которые реализуются DE:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  EE работает [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2`обеспечивает механизм описания результата оценки выражения, например, локальную переменную, примитивную или объект Visual Studio, которая затем отображает соответствующую информацию в **locals,** **Watch**или **Immediate** window.

  SP дается EE DE, когда он запрашивает информацию. SP запускает интерфейсы, описывающие адреса и поля, такие как следующие интерфейсы и их производные:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE потребляет все эти интерфейсы.

## <a name="in-this-section"></a>В этом разделе
 [Стратегия реализации оценки экспрессии](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) Определяет трехступенчатый процесс для стратегии реализации оценщика выражения (EE).

## <a name="see-also"></a>См. также
- [Написание оценщика экспрессии CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
