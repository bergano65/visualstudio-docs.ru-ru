---
title: "IEEVisualizerService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerService"
helpviewer_keywords: 
  - "Интерфейс IEEVisualizerService"
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IEEVisualizerService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс реализует основные методы, которые предоставляют функциональные возможности для [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) и [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) интерфейсов.  
  
## Синтаксис  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## Примечания для разработчиков  
 Visual Studio реализует этот интерфейс, позволяющий вычислитель выражений \(EE\) для поддержки типа визуализаторы.  
  
## Примечания для вызывающих объектов  
 Вызовы EE [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) получить этот интерфейс как часть поддержки для типа визуализаторы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Возвращает число пользовательских средств просмотра, о которых известно, эта служба.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Получает список пользовательских средств просмотра.|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Возвращает объект прокси для свойства.|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Получает номер строки значение указанного свойства или поля.|  
  
## Заметки  
 Интегрированная среда разработки использует [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс, чтобы определить любые пользовательские средства просмотра или введите визуализаторы для свойства. После создания визуализатора службы \(с [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)\), EE можно предоставить возможность `IDebugProperty3` и [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) \(который поддерживает просмотр и изменение значения свойства\) интерфейсы и тем самым поддерживает тип визуализаторы.  
  
 Если EE пользовательских средств просмотра, в свою очередь реализует, можно добавить EE `CLSID`s из этих пользовательских средств просмотра, в конец списка, возвращаемый [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). Это позволяет EE для поддержки типа визуализаторы и свои собственные пользовательские средства просмотра. Просто убедитесь, что [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) получающийся при добавлении любые пользовательские средства просмотра.  
  
 В разделе [Тип визуализатора и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Обсуждение разница между визуализаторы и средства просмотра.  
  
## Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы вычисление выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [Тип визуализатора и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)