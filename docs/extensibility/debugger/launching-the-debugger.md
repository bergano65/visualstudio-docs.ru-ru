---
title: "Запуск отладчика | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [пакет SDK для отладки], запуск отладчика"
  - "отладчик [пакет SDK для отладки], запуск"
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Запуск отладчика
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Запуск отладчика требуется отправлять правильную последовательность методов и событий с правильными атрибутами.  
  
## Последовательность методов и событий  
  
1.  Сеанс отладки \(SDM\) диспетчер вызывается путем выбора **Отладка** меню, а затем выбрав  **Запуск**.  Дополнительные сведения см. в разделе [Запуск программы](../../extensibility/debugger/launching-a-program.md).  
  
2.  Вызовы SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод.  
  
3.  В зависимости от модели процессов обработчика отладки \(DE\) `IDebugProgramNodeAttach2::OnAttach` метод возвращает один из следующих методов, указывающее, что происходит далее.  
  
     If `S_FALSE` возвращает обработчик отладки \(DE\) загруженной в процесс виртуальной машине.  
  
     \-или\-  
  
     If `S_OK` возвращает DE необходимо загрузить в процессе SDM.  SDM затем выполняет следующие задачи:  
  
    1.  Вызовы [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) получить данные обработчика DE.  
  
    2.  DE Co\-создаст.  
  
    3.  Вызывает [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  DE отправляет [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) в SDM с  `EVENT_SYNC` атрибут.  
  
5.  DE отправляет [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) в SDM с  `EVENT_SYNC` атрибут.  
  
6.  DE отправляет [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) в SDM с  `EVENT_SYNC` атрибут.  
  
7.  DE отправляет [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) в SDM с  `EVENT_SYNC` атрибут.  
  
8.  DE отправляет [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) в SDM с  `EVENT_SYNC` атрибут.  
  
## См. также  
 [Вызов события отладчика](../../extensibility/debugger/calling-debugger-events.md)   
 [Запуск программы](../../extensibility/debugger/launching-a-program.md)