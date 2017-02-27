---
title: "Присоединение к программе | Microsoft Docs"
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
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Присоединение к программе
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

После регистрации собственного приложения с соответствующим портом, нужно вложить отладчик в программе требуется отладить.  
  
## Выбрать, Как вложение  
 3 Способа, в котором сеанс отладки попытки диспетчера \(SDM\) вложение в отлаживаемом программе.  
  
1.  Для программ, которые запускаются с помощью обработчика отладки [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) метод \(типичный интерпретированных языков, например\), SDM возвращает  [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) интерфейс из  [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) объект, связанный с вложенным, программа.  Если SDM может получать `IDebugProgramNodeAttach2` интерфейс SDM затем вызывает метод  [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод.  `IDebugProgramNodeAttach2::OnAttach` метод возвращает  `S_OK` показать, что он не вложил в программе, а остальные попытки можно сделать, чтобы вложить в программе.  
  
2.  Если SDM может получать [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) интерфейс из программы, вложенным в SDM вызывает  [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) метод.  Этот подход является типичным для программ, которые были запущены удаленно поставщика порта.  
  
3.  Если программа не может быть вложен между `IDebugProgramNodeAttach2::OnAttach` OR  `IDebugProgramEx2::Attach` методы, загружающие обработчик отладки \(SDM, если оно еще не загружен\) путем вызова  `CoCreateInstance` функция а затем вызовите  [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) метод.  Этот подход является типичным для программ, запущенных локально поставщика порта.  
  
     Также возможно для пользовательского поставщика порта вызова `IDebugEngine2::Attach` метод при реализации пользовательского поставщика порта  `IDebugProgramEx2::Attach` метод.  Обычно в этом случае пользовательский поставщик порта запускает средство отладки на удаленном компьютере.  
  
 Вложение достичь, если сеанс отладки вызовы диспетчера \(SDM\) [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) метод.  
  
 Если используется пользовательский DE в том же процессе какого приложение быть отлаживанным, необходимо реализовать следующие методы IDebugProgramNode2.  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 После `IDebugEngine2::Attach` метод вызывается, выполните следующие шаги в реализации  `IDebugEngine2::Attach` метод:  
  
1.  Send IDebugEngineCreateEvent2 объект события в SDM.  Дополнительные сведения см. в разделе [Отправка событий](../../extensibility/debugger/sending-events.md).  
  
2.  Вызовите [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) метод  [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) объект, который был передан  `IDebugEngine2::Attach` метод.  
  
     Это возвращает a `GUID` используется для указания программы.  `GUID` храниться в объекте, представляющий локальную программы с DE и его, если необходимо возвращать  `IDebugProgram2::GetProgramId` метод вызывается во  `IDebugProgram2` интерфейс.  
  
    > [!NOTE]
    >  При реализации `IDebugProgramNodeAttach2` интерфейс, программа  `GUID` передает в  `IDebugProgramNodeAttach2::OnAttach` метод.  This `GUID` использование программы  `GUID` возвращается  `IDebugProgram2::GetProgramId` метод.  
  
3.  Send [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) объект события для оповещения SDM, локальное  `IDebugProgram2` объект создан для представления программы с DE.  Дополнительные сведения см. в разделе [Отправка событий](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    >  Это не то же `IDebugProgram2` объект, который был передан в  `IDebugEngine2::Attach` метод.  Ранее переданный `IDebugProgram2` объект портом и только отдельным объектом.  
  
## См. также  
 [На основе запуска вложения](../../extensibility/debugger/launch-based-attachment.md)   
 [Отправка событий](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)