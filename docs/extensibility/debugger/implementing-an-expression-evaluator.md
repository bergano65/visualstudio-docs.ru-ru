---
title: Реализация вычислителя выражений | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e468c24690926cef62ba56e7b58a178580f90490
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411256"
---
# <a name="implement-an-expression-evaluator"></a>Реализация вычислителя выражений
> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образец средства оценки выражений управляемый](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Вычисления выражения является сложным взаимодействием между модуль отладки (DE), поставщик символов (SP), объект модуля привязки и средство оценки выражений (EE). Эти четыре компонента соединены с интерфейсами, реализованный в одном компоненте и использованы другим.

 EE принимает выражение из DE в виде строки и анализирует и оценивает его. EE запускает следующие интерфейсы, которые могут использоваться DE:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  EE вызывает объект связыватель, предоставленный DE, чтобы получить это значение, символы и объектов. EE использует следующие интерфейсы, реализуемые с DE:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  Запускает EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` предоставляет механизм для описания результат вычисления выражения, такие как локальная переменная, примитив или объект для Visual Studio, которая затем отображает соответствующую информацию в **"Локальные"**, **контрольных значений** , или **Интерпретация** окна.

  SP присваивается EE путем DE, когда он запрашивает сведения. Хранимая процедура выполняется интерфейсы, которые описывают адреса и поля, такие как следующие интерфейсы, а также производных:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE использует все эти интерфейсы.

## <a name="in-this-section"></a>Содержание раздела
 [Стратегия реализации вычислителя выражений](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) определяет трехшаговый процесс стратегия реализации вычислителя (EE) выражений.

## <a name="see-also"></a>См. также
- [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)