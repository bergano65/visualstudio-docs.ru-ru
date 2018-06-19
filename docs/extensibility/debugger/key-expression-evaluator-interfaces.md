---
title: Основные интерфейсы вычислителя выражений | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe0c592c65e2c6ab7429cef44a830325a834ecdc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103852"
---
# <a name="key-expression-evaluator-interfaces"></a>Интерфейсы вычислителя выражения ключа
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 При написании вычислитель выражений (Эстония) вместе с контекстом оценки, необходимо ознакомиться с следующие интерфейсы.  
  
## <a name="interface-descriptions"></a>Описание интерфейса  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     Содержит один метод [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), который возвращает структуру данных, представляющий текущей точки выполнения. Эта структура данных является одним из трех аргументов, которые передает модуль отладки (DE) [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) метод для вычисления выражения. Обычно этот интерфейс реализуется поставщиком символа.  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     Имеет [привязки](../../extensibility/debugger/reference/idebugbinder-bind.md) метод, который получает области памяти, содержащей текущее значение символа. Оба содержащего метода, представленного заданным [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) объект и самого символа, представленного [IDebugField](../../extensibility/debugger/reference/idebugfield.md) объекта, `IDebugBinder::Bind` возвращает значение символа. `IDebugBinder` обычно реализуется DE.  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     Представляет простой тип данных. Для более сложных типов, таких как массивы и методы, используйте производный [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) и [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) интерфейсы, соответственно. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) — другой важные производный интерфейс, представляющий содержащий других символов, например методов или классов символов. `IDebugField` Поставщиком символ обычно реализуется интерфейс (и производные от него).  
  
     `IDebugField` Объект можно использовать для поиска имени и типа символа и, вместе с [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) объекта, можно использовать для поиска его значение.  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     Представляет число битов во время выполнения значения символа. [Привязать](../../extensibility/debugger/reference/idebugbinder-bind.md) принимает [IDebugField](../../extensibility/debugger/reference/idebugfield.md) объекта, представляющего символ, и возвращает [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) объекта. [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) метод возвращает значение символа в буфере памяти. DE обычно реализует этот интерфейс для представления значения свойства в памяти.  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     Этот интерфейс представляет сам средство оценки выражений. Основной метод — [проанализировать](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), который возвращает [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) интерфейса.  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     Этот интерфейс представляет проанализированное выражение, готовое к вычислению. Основной метод — [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) который возвращает значение IDebugProperty2, представляющий значение и тип выражения.  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     Этот интерфейс представляет значение, а его тип и является результатом вычисления выражения.  
  
## <a name="see-also"></a>См. также  
 [Контекст вычислений](../../extensibility/debugger/evaluation-context.md)