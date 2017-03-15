---
title: "Контекст оценки | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [отладка SDK], вычисление выражений"
  - "вычисление выражений, контекст"
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Контекст оценки
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Когда отладчик \(DE\) вызывает вычислитель выражений \(EE\), три аргументы, передаваемые [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) определить контекст для поиска и оценке символы, как показано в следующей таблице.  
  
## Аргументы  
  
|Аргумент|Описание|  
|--------------|--------------|  
|`pSymbolProvider`|[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) Интерфейс, который определяет обработчик символ \(SH\) для определения символа.|  
|`pAddress`|[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) Интерфейс, определяющий текущей точки выполнения. Это можно использовать для поиска метода, содержащего выполняемый код.|  
|`pBinder`|[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) Интерфейс, который может использоваться для поиска символов, заданную ее именем типа и значения.|  
  
 `IDebugParsedExpression::EvaluateSync` Возвращает [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс, представляющий результирующее значение и тип.  
  
## См. также  
 [Интерфейсы вычислителя выражения ключа](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)