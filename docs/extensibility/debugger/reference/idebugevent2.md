---
title: "IDebugEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEvent2"
helpviewer_keywords: 
  - "Интерфейс IDebugEvent2"
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс используется для обмена данными и критическое отладочные данные, как остановить в точке останова и некритическое сведения, как сообщение отладки.  
  
## Синтаксис  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) и пользовательского поставщика порта реализовать этот интерфейс на одном объекте как любые другие интерфейсы событий.  
  
## Замечания для вызывающих объектов  
 Использование аргумент идентификатор интерфейса \(IID\), который дан объекту [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) OR  [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)сеанс отладки вызовы диспетчера \(SDM\)  [QueryInterface](/visual-cpp/atl/queryinterface) на  `IDebugEvent2` интерфейс, чтобы получить нужный интерфейс событий.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugEvent2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Получает атрибуты этого события отладки.|  
  
## Заметки  
 Интерфейсы события, определенные как [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)не наследуется от интерфейса IDebugEvent2 а вместо этого необходимо реализовать в виде отдельного интерфейса в одном объекте как  `IDebugEvent2`.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)