---
title: "Интерфейсы вычислителя выражения ключа | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [отладка SDK], вычисление выражений"
  - "вычисление выражений, интерфейсы"
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Интерфейсы вычислителя выражения ключа
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 При написании вычислитель выражений \(EE\) вместе с контекстом оценки, необходимо ознакомиться с следующие интерфейсы.  
  
## Описание интерфейса  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     Содержит один метод [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), который возвращает структуру данных, представляющий текущей точки выполнения. Эта структура данных является одним из трех аргументов, отладчик \(DE\) передает [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) метод для вычисления выражения. Этот интерфейс обычно реализуется поставщиком символов.  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     Имеет [Привязка](../../extensibility/debugger/reference/idebugbinder-bind.md) метод, который получает области памяти, которая содержит текущее значение символа. Оба содержащего метод, представленный [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) объект и самого символа, представленного [IDebugField](../../extensibility/debugger/reference/idebugfield.md) объекта, `IDebugBinder::Bind` возвращает значение символа.`IDebugBinder` обычно реализуется DE.  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     Представляет простой тип данных. Для более сложных типов, таких как массивы и методы, используйте производный [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) и [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) интерфейсы, соответственно.[IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) другой важной производный интерфейс, представляющий символы, содержащий другие символы, такие как методы или классы.`IDebugField` Интерфейс \(и его производные\) обычно реализуется поставщиком символов.  
  
     `IDebugField` Объект можно использовать поиск имени и типа символа и, вместе с [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) объекта, можно использовать для поиска его значение.  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     Представляет число битов во время выполнения значения символа.[Привязка](../../extensibility/debugger/reference/idebugbinder-bind.md) принимает [IDebugField](../../extensibility/debugger/reference/idebugfield.md) объект, который представляет символа и возвращает [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) объекта.[GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) Метод возвращает значение символа в буфере памяти. DE обычно реализует этот интерфейс для представления значения свойства в памяти.  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     Этот интерфейс представляет сам средство оценки выражений. Основной метод — [Анализ](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), который возвращает [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) интерфейса.  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     Этот интерфейс представляет проанализированное выражение, готовое к вычислению. Основной метод — [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) который возвращает значение IDebugProperty2, предоставляющий значение и тип выражения.  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     Этот интерфейс представляет значение и тип и является результатом вычисления выражения.  
  
## См. также  
 [Контекст оценки](../../extensibility/debugger/evaluation-context.md)