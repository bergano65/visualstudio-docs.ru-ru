---
title: Выражения вычисления интерфейсы | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a5ce9f82e88c6275000c17d40e2b1e1494683715
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="expression-evaluation-interfaces"></a>Интерфейсы вычисление выражений
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ниже перечислены интерфейсы вычисления выражения для [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пакет SDK для отладки.  
  
## <a name="discussion"></a>Обсуждение  
 Эти интерфейсы используются для вычисления выражений в стеке вызова в режиме приостановки выполнения. Они реализуются только для общих вычислители выражений во время выполнения языка (EE).  
  
 Каждый интерфейс в таблице показан компонент, который можно реализовать из следующего списка:  
  
-   Отладка ядра (DE)  
  
-   Вычислитель выражений (Эстония)  
  
-   Visual Studio (VS)  
  
|Интерфейс|Реализуемый|Описание:|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Представляет числовой псевдоним для переменной.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Представляет числовой псевдоним для переменной и обеспечивает вычислитель выражений (EE), чтобы получить домен приложения для псевдонима.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Представляет объект массива.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Представляет объект управляемого массива и позволяет вычислитель выражений (EE), чтобы определить базовый индекс массива (нижние границы).|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Представляет привязку, что привязки отладочных символов в фактические адреса в памяти.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|То же, что [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) интерфейс но предоставляет доступ к типам, псевдонимы и пользовательских визуализаторов.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Представляет средство оценки выражений.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Представляет улучшенной версии вычислитель выражений (EE).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Представляет средство оценки выражений (EE) с деревом улучшенные средства синтаксического анализа.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Представляет функцию.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Представляет функцию и повышает [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) интерфейса.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Позволяет вычислитель выражений (EE) отобразить сообщение в окне вывода.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Представляет объект управляемого кода.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Базовый интерфейс, представляющий любой символ привязан к адресу памяти.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|То же, что [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейс, но обеспечивает доступ к дополнительной информации.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Представляет проанализированное выражение, готовое к вычислению.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Представляет указатель.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Представляет указатель в дерево синтаксического анализа и расширяет возможности **IDebugPointerObject** интерфейса.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Предоставляет возможность изменять значения типа через тип визуализатора.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Предоставляет доступ к пользовательских средств просмотра и визуализаторами типов.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Предоставляет возможность создавать [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) объекта.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Представляет коллекцию [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объектов.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Написание выражений CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)