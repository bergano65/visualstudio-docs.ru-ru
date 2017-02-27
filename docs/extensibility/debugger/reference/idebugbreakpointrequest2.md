---
title: "IDebugBreakpointRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointRequest2"
helpviewer_keywords: 
  - "Интерфейс IDebugBreakpointRequest2"
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugBreakpointRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет сведения, необходимые для создания и привязали любой тип точки останова.  
  
## Синтаксис  
  
```  
IDebugBreakpointRequest2 : IUnknown  
```  
  
## Примечания по реализации  
 Сеанс отладки \(SDM\) диспетчер обычно реализует этот интерфейс.  
  
## Замечания для вызывающих объектов  
 Отладчик \(DE\) возвращает этот интерфейс через вызов [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) создание ожидается точка останова.  Вызов [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) может получить этот интерфейс с DE.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugBreakpointRequest2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Возвращает тип расположения точки останова этого запроса точки останова.|  
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Возвращает сведения о запросе точки останова, описывающее этот запрос точки останова.|  
  
## Заметки  
 Выберите, отлаживанными программы загружает вызов [Привязка](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) привязывает отложенную точку останова в местоположение для запрошенного в программе.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)   
 [Привязка](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)