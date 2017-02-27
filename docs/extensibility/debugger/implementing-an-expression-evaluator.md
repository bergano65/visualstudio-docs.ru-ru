---
title: "Реализация вычислитель выражений | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "вычислители выражений"
  - "отладка [отладка SDK] вычислители выражений"
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Реализация вычислитель выражений
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Оценка выражения является сложным взаимодействием между ядра отладки \(DE\), поставщик символов \(SP\), объект привязки и вычислитель выражений \(EE\) сам. Интерфейсы, реализованные в один компонент и использован другим соединенных этих четырех компонентов.  
  
 EE принимает выражение из DE в виде строки и анализирует и выполняет его оценку. EE реализует следующие интерфейсы, которые потребляются DE.  
  
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
  
 Реализует EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md).`IDebugProperty2` предоставляет механизм для описания результата вычисления выражения, такие как локальную переменную, примитив или объект, в Visual Studio, которая затем отображает соответствующую информацию в **Локальные**, **Контрольные значения**, или **Интерпретация** окна.  
  
 SP присваивается EE путем DE, когда он запрашивает сведения. SP реализует интерфейсы, которые описывают адреса и полей, таких как следующие интерфейсы и их производные:  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 EE использует все эти интерфейсы.  
  
## В этом подразделе  
 [Стратегия реализации вычислителя выражений](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Определяет три этапа, для реализации стратегии оценки \(EE\) выражения.  
  
## См. также  
 [Написание вычислитель выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)