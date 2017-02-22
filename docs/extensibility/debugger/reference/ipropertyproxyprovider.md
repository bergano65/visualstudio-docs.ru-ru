---
title: "IPropertyProxyProvider | Microsoft Docs"
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
  - "IPropertyProxyProvider"
helpviewer_keywords: 
  - "Интерфейс IPropertyProxyProvider"
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IPropertyProxyProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Предоставляет этого интерфейса интерфейс прокси\-сервера, чтобы просмотреть и изменить данные объекта.  
  
## Синтаксис  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## Примечания по реализации  
 Средство оценки выражений \(EE\) реализует этот интерфейс на одном и том же объекта, реализующего [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс как часть поддержки EE визуализаторов типа.  
  
## Замечания для вызывающих объектов  
 Вызов [QueryInterface](/visual-cpp/atl/queryinterface) на  `IDebugProperty3` интерфейс для получения этого интерфейса.  
  
## Методы в том порядке Vtable  
 `IPropertyProxyProvider` интерфейс реализован следующий метод:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Извлекает интерфейс прокси свойства, чтобы просмотреть данные в объекте.|  
  
## Заметки  
 Хотя EE реализующий этот интерфейс, реализация [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) обычно обрабатывается by  [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md).  См. [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) дополнительные сведения о получении интерфейс IEEVisualizerService.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Тип визуализатора и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)