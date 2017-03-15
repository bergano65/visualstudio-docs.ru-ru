---
title: "Присоединение и отсоединение программы | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладчики, присоединение к программам"
  - "отладчики, отсоединение от программы"
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Присоединение и отсоединение программы
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Вложение отладчика требуется отправлять правильную последовательность методов и событий с правильными атрибутами.  
  
## Последовательность методов и событий  
  
1.  Сеанс отладки вызовы диспетчера \(SDM\) [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод.  
  
     В зависимости от модели процессов обработчика отладки \(DE\) `IDebugProgramNodeAttach2::OnAttach` метод возвращает один из следующих методов, указывающее, что происходит далее.  
  
     If `S_FALSE` возвращает обработчик отладки успешно вложение в программе.  В противном случае \- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) метод вызывается для выполнения процесса вложить.  
  
     If `S_OK` возвращает DE быть загружен в том же процессе, что и SDM.  SDM выполняет следующие задачи:  
  
    1.  Вызовы [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) получить данные обработчика DE.  
  
    2.  DE Co\-создаст.  
  
    3.  Вызывает [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2.  DE отправляет [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) в SDM с  `EVENT_SYNC` атрибут.  
  
3.  DE отправляет [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) в SDM с  `EVENT_SYNC` атрибут.  
  
4.  DE отправляет [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) в SDM с  `EVENT_SYNC_STOP` атрибут.  
  
 Наконец удалить из программы простой процесс шага 2, следующим образом:  
  
1.  Вызовы SDM [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
2.  DE отправляет IDebugProgramDestroyEvent2.  
  
## См. также  
 [Вызов события отладчика](../../extensibility/debugger/calling-debugger-events.md)