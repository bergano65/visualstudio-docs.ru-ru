---
title: Интерфейсы оценки выражения | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74e65d56701aaa2e9a864d822cb7b44435e2bb09
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55024257"
---
# <a name="expression-evaluation-interfaces"></a>Интерфейсы вычисления выражений
> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ниже перечислены интерфейсы оценки выражения [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] отладки пакета SDK.  
  
## <a name="discussion"></a>Обсуждение  
 Эти интерфейсы используются для оценки выражений, в стеке вызовов в режиме приостановки выполнения. Они реализуются только для общих-язык вычислители выражений во время выполнения (EE).  
  
 Каждый интерфейс в таблице показан компонент, который можно реализовать из следующего списка:  
  
-   Отладка ядра (DE)  
  
-   Средство оценки выражений (EE)  
  
-   Visual Studio (VS)  
  
|Интерфейс|Реализуется|Описание|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Представляет числовые псевдоним для переменной.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Представляет числовые псевдоним для переменной и обеспечивает вычислитель выражений (EE), чтобы получить домен приложения для псевдонима.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Представляет объект массива.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Представляет объект управляемого массива и позволяет вычислитель выражений (EE), чтобы определить базовый индекс (нижней границы) для массива.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Представляет привязку, что привязки отладочные символы для фактические адреса в памяти.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Совпадение с кодом [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) интерфейс, но обеспечивает доступ к типам, псевдонимы и пользовательских визуализаторов.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Представляет средство оценки выражений.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Представляет улучшенная версия вычислитель выражений (EE).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Представляет средство оценки выражений (EE) с деревом улучшенные средства синтаксического анализа.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Представляет функцию.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Представляет функцию и улучшает [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) интерфейс.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Позволяет вычислитель выражений (EE) для отображения сообщения в окне вывода отладчика.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Представляет объект управляемого кода.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Базовый интерфейс, представляющий любой символ привязан к адресу памяти.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Совпадение с кодом [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейс, но предоставляет доступ к дополнительной информации.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Представляет проанализированное выражение, готовое к вычислению.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Представляет указатель.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Представляет указатель в дерево синтаксического анализа и расширяет **IDebugPointerObject** интерфейс.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Предоставляет возможность изменить значение типа с помощью типа визуализатора.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Предоставляет доступ к пользовательских средств просмотра и визуализаторами типов.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Предоставляет возможность создания [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) объекта.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Представляет коллекцию [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объектов.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Запись вычислителя выражений CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)