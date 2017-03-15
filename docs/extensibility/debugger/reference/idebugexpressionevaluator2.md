---
title: "IDebugExpressionEvaluator2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugExpressionEvaluator2"
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugExpressionEvaluator2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Представляет расширенную версию вычислитель выражений \(EE\).  
  
## Синтаксис  
  
```  
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator  
```  
  
## Примечания для разработчиков  
 Этот интерфейс реализуется в средстве оценки выражений.  
  
## Методы  
 В дополнение к методам на [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) интерфейс, этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Получает объект службы, учитывая его уникального идентификатора.|  
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Предварительно загружает модули, заданное поставщиком указанного символа.|  
|[SetCallback](../Topic/IDebugExpressionEvaluator2::SetCallback.md)|Включает средство оценки выражений \(EE\) для указания интерфейс обратного вызова, который ядро отладки \(DE\) будет использовать для чтения параметры метрик.|  
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Задает путь к общеязыковой среды выполнения \(CLR\), загрузить в отладчик.|  
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Включает отладчик для передачи обратного вызова для вычислителя выражения во время инициализации.|  
|[Завершить](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|Останавливает и удаляет средство оценки выражений.|  
  
## Требования  
 Заголовок: Ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll