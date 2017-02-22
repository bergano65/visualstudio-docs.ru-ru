---
title: "IDebugBreakpointRequest3 | Microsoft Docs"
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
  - "IDebugBreakpointRequest3"
helpviewer_keywords: 
  - "IDebugBreakpointRequest3"
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointRequest3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет сведения, необходимые для создания и привязали любой тип точки останова.  Расширение  [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).  
  
## Синтаксис  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## Примечания по реализации  
 Сеанс отладки \(SDM\) диспетчер обычно реализует этот интерфейс.  
  
## Замечания для вызывающих объектов  
 Отладчик \(DE\) обращается к этого интерфейса нужно вызвать метод [QueryInterface](/visual-cpp/atl/queryinterface) в интерфейсе IDebugBreakpointRequest2 получил вызову  [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).  
  
## Методы в том порядке Vtable  
 В дополнение к методам, наследуемым от интерфейса [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), интерфейс `IDebugBreakpointRequest3` предоставляет следующий метод.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Возвращает сведения о запросе точки останова, описывающее этот запрос точки останова.|  
  
## Заметки  
 Этот интерфейс используется для реализации дополнительной информации через DE [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структура.  Эта дополнительная информация включает идентификатор поставщика DE \(в форме GUID\), имя точки трассировки и имя ограничения точки останова.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)