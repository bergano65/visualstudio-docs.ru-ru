---
title: "Интерфейсы вычисление выражений | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "вычисление выражений, интерфейсы"
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Интерфейсы вычисление выражений
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ниже перечислены интерфейсы оценки выражения для [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пакет SDK для отладки.  
  
## Обсуждение  
 Эти интерфейсы используются для вычисления выражений в стек вызовов в режиме приостановки выполнения. Они реализуются только для общих вычислители выражений во время выполнения языка \(EE\).  
  
 Каждый интерфейс в таблице показан компонент, который можно реализовать в следующем списке:  
  
-   Отладка ядра \(DE\)  
  
-   Вычислитель выражений \(EE\)  
  
-   Visual Studio \(VS\)  
  
|Интерфейс|Реализованный|Описание|  
|---------------|-------------------|--------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Представляет числовые псевдоним для переменной.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Представляет числовые псевдоним для переменной и позволяет вычислитель выражений \(EE\), чтобы получить домен приложения для псевдонима.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Представляет объект массива.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Представляет объект управляемого массива и позволяет вычислитель выражений \(EE\) для определения базового индекса \(нижней границы\) для массива.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Представляет привязку, что привязки отладочных символов для фактические адреса в памяти.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|То же, что [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) интерфейс но предоставляет доступ к типам, псевдонимы и пользовательских визуализаторов.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Представляет средство оценки выражений.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Представляет расширенную версию вычислитель выражений \(EE\).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Представляет средство оценки выражений \(EE\) с деревом улучшенные средства синтаксического анализа.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Представляет функцию.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Представляет функцию и улучшает [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) интерфейса.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Включает средство оценки выражений \(EE\) для отображения сообщения в окне вывода отладчика.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Представляет объект управляемого кода.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Базовый интерфейс, представляющий любой символ привязан к адресу памяти.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|То же, что [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейс, но предоставляет доступ к дополнительной информации.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Представляет проанализированное выражение, готовое к вычислению.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Представляет указатель.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Представляет указатель в дерево синтаксического анализа и расширяет **IDebugPointerObject** интерфейса.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Предоставляет возможность изменить значение типа с помощью визуализатора типа.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Предоставляет доступ к пользовательских средств просмотра и тип визуализаторы.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Предоставляет возможность создания [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) объекта.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Представляет коллекцию объектов [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md).|  
  
## См. также  
 [Справочник по интерфейсам API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Написание вычислитель выражений CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Тип визуализатора и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)