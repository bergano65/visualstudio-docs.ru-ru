---
title: "IDebugCanStopEvent2 | Microsoft Docs"
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
  - "IDebugCanStopEvent2"
helpviewer_keywords: 
  - "Интерфейс IDebugBreakpointRequest2"
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCanStopEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс, чтобы запросить сеансу отладки \(SDM\), используется ли диспетчер остановки в текущем расположении кода.  
  
## Синтаксис  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс, чтобы поддерживать пошаговой отладки исходный код.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован в одном объекте, как этот интерфейс \(SDM использует  [QueryInterface](/visual-cpp/atl/queryinterface) доступ  `IDebugEvent2` интерфейс\).  
  
 Реализация этого интерфейса должна взаимодействовать вызов SDM [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) в обработчик отладки.  Например, это можно делать с сообщением, созданное в поток сообщений обработчика отладки или объект, реализующий этот интерфейс, может содержать ссылку на обработчик и вызову отладки назад в обработчик отладки с пометить переданный в `IDebugCanStopEvent2::CanStop`.  
  
## Замечания для вызывающих объектов  
 DE может отправлять этот метод, каждый раз будет предложено продолжает DE выполнение и DE шагает посредством кода.  Это событие отправляется с помощью IDebugEventCallback2 функция обратного вызова, предоставляемая SDM, когда он вложен в отлаживаемом программе.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugCanStopEvent2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetReason](../Topic/IDebugCanStopEvent2::GetReason.md)|Возвращает причину данного события.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Указывает, должна ли отлаживаемой программы остановки на месте этого события \(и отправить событие, описывающее причину для остановки\) или просто возобновить выполнение.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Возвращает контекст рисования, описывающий расположение данного события.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Возвращает контекст кода, описывающий расположение данного события.|  
  
## Заметки  
 DE отправляет этот интерфейс, если действия пользователя в функцию и DE не находящихся в ней нет сведений отладки или отладочные данные существуют, но DE не знает, если исходный код может отображаться для этого расположения.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)