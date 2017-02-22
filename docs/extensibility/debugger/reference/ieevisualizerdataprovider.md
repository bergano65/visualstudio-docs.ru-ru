---
title: "IEEVisualizerDataProvider | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerDataProvider"
helpviewer_keywords: 
  - "Интерфейс IEEVisualizerDataProvider"
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerDataProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс предоставляет возможность изменить значение объекта с помощью визуализатора типа.  
  
## Синтаксис  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## Примечания для разработчиков  
 Средство оценки выражений реализует этот интерфейс для поддержки изменения данных на объект свойства через тип визуализатора.  
  
## Примечания для вызывающих объектов  
 Этот интерфейс служит для создания [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) объекта путем вызова [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Дополнительные сведения см. в разделе [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md).  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[CanSetObjectForVisualizer](../Topic/IEEVisualizerDataProvider::CanSetObjectForVisualizer.md)|Определяет, можно обновить объект \(и следовательно, его значение\), представляющий этот визуализатор.|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Принудительное повторное вычисление объект для этого визуализатора.|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Возвращает объект для этот визуализатор \(оценка не выполняется\).|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Обновляет объект для этого визуализатор, тем самым изменив значение, которое представляет визуализатора.|  
  
## Заметки  
 Служба визуализатора \(представленные как [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) интерфейс и возвращенный [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)\) хранит ссылку на объект, реализующий `IEEVisualizerDataProvider` интерфейса. В результате `IEEVisualizerDataProvider` не следует реализовывать на тот же объект, реализующий интерфейс [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Если этот объект содержит ссылку на `IEEVisualizerService` объект: циклическая ссылка и Взаимоблокировка возникает, когда объекты уничтожаются. Рекомендуется реализовать `IEEVisualizerDataProvider` на отдельный объект, к которому `IDebugProperty2` объекта делегаты без вызова `IUnknown::AddRef` на нем.  
  
## Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы вычисление выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)