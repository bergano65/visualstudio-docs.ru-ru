---
title: Реализация вычислитель выражений | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed1df74c187b3f0a93e1a1ec84e8803bc164d223
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-an-expression-evaluator"></a>Реализация вычислитель выражений
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Вычисления выражения является сложное взаимодействие между модуль отладки (DE), символ поставщика услуг, объект модуля привязки и средство оценки выражений (Эстония) сам. Эти четыре компонента соединены с интерфейсов, реализованного в одном компоненте и использован другим.  
  
 EE принимает выражение из DE в виде строки и анализирует или вычисляет его. EE реализует следующие интерфейсы, которые могут использоваться DE.  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
 EE вызывает объект привязки, предоставляемые DE, для получения значения символов и объекты. EE использует следующие интерфейсы, реализуемые с DE:  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
-   [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
-   [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
-   [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
-   [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
-   [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
 Реализует EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` предоставляет механизм для описания результат вычисления выражения, такие как локальную переменную, примитивом или объекте, в Visual Studio, которые затем отображаются соответствующие сведения в **локальные**,  **Контрольное значение**, или **Интерпретация** окна.  
  
 SP присваивается EE путем DE, когда он запрашивает сведения. SP реализует интерфейсы, которые описывают адреса и полей, таких как следующие интерфейсы, а также производных:  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 EE использует все эти интерфейсы.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Стратегия реализации вычислителя выражений](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Определяет трехступенчатый процесс для реализации стратегии оценки (Эстония) выражения.  
  
## <a name="see-also"></a>См. также  
 [Написание выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)