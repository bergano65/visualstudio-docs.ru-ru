---
title: "Методы, связанные с точки останова | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "точка останова методов отладки [отладка SDK]"
  - "точки останова, методы"
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Методы, связанные с точки останова
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Отладчик \(DE\) должен поддерживать параметр точек останова.  Отладка Visual Studio поддерживает следующие типы точек останова.  
  
-   Связанный режим  
  
     Запрашивает через пользовательский интерфейс и успешно границы в указанное расположение кода  
  
-   Ожидание  
  
     Запрашивает через пользовательский интерфейс, но еще не границы к фактическим инструкции  
  
## Обсуждение  
 Например, ожидается точка останова происходит, когда инструкции еще не загружены.  Если код загружен, ожидающие точки останова попробуйте выполнить привязку к коду на предписанном месте хранения, т е в инструкции insert останова в коде.  События передаются в сеанс отладки \(SDM диспетчер\), чтобы показать успешные привязку или уведомить что привязали ошибки.  
  
 Ожидается точка останова также управляет свой внутренний список соответствующих связанных точек останова.  Один ожидающий точки останова может вызвать insert много точек останова в коде.  Пользовательский интерфейс отладки Visual Studio содержит представление в виде дерева ожидающих точек останова и соответствующих связанных точек останова.  
  
 Создание и использование ожидающих точки останова требует реализации [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) метод а также следующие методы  [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) интерфейсы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Определяет, является ли указанное в очереди точки останова может привязать к местоположению кода.|  
|[Привязка](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Привязывает указанное в очереди точки останова с одним или несколькими места кода.|  
|[GetState](../Topic/IDebugPendingBreakpoint2::GetState.md)|Получает состояние отложенной точки останова.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Возвращает запрос точки останова, используемый для создания ожидается точка останова.|  
|[Включить](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Переключает включенное состояние отложенной точки останова.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Перечисляет все точки останова из привязанные ожидающих точки останова.|  
|[EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md)|Перечисляет все точки останова ошибки, полученные в результате, ожидающих точки останова.|  
|[Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Удаляет отложенную точку останова и все точки останова привязанные из нее.|  
  
 Чтобы перечислить связанные точки останова и точки останова ошибки, необходимо реализовать все методы [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) и   [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).  
  
 Ожидающие точек останова, которые должны быть привязаны к местоположению кода требует реализации следующих элементов IDebugBoundBreakpoint2 методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetPendingBreakpoint](../Topic/IDebugBoundBreakpoint2::GetPendingBreakpoint.md)|Получает завершения отложенной точку останова, содержащей точку останова.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Получает состояние связанной точки останова.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Возвращает разрешение точки останова, описывающее точку останова.|  
|[Включить](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Позволяет включить или отключить точку останова.|  
|[Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Удаляет связанную точка останова.|  
  
 Данные разрешения и требует реализации следующих запроса IDebugBreakpointResolution2 методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Возвращает тип точки останова, представленный разрешением.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Возвращает сведения о разрешениях точки останова, описывающее точку останова.|  
  
 Разрешение ошибок, которые могут произойти во время привязки требует реализации следующих элементов IDebugErrorBreakpoint2 методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Получает завершения отложенной точку останова, которая содержит точку останова ошибки.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Возвращает разрешение ошибок точки останова, описывающее точку останова ошибки.|  
  
 Разрешение ошибок, которые могут произойти во время привязки также требует следующих методов IDebugErrorBreakpointResolution2.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Возвращает тип точки останова.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Возвращает сведения о разрешениях точки останова.|  
  
 Просмотреть исходный код на точке останова, требует реализации методов [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) и\/или методы   [IDebugStackFrame2:: GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md).  
  
## См. также  
 [Управление выполнением и оценки состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)