---
title: "Присоединение после запуска | Microsoft Docs"
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
  - "отладчики, присоединение к программам"
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Присоединение после запуска
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

После того, как программа запущена, сеанс отладки можно вложить отладчик \(DE\) в сказанной программе.  
  
## Проектирование решений  
 Так как сообщение проще в общем адресное пространство, необходимо определить, выполняет ли оно больше чувства упростить взаимодействие между сеансами отладки и DE или между DE и приложениями.  Выбор между следующими параметрами:  
  
-   Если она выполняет несколько чувства упростить взаимодействие между сеансами отладки и DE, то сеанс отладки co\-создаст DE и запрашивает DE, чтобы вложить в программе.  Это оставляет сеанс отладки и DE в одно адресное пространство и среду выполнения и в другие программы.  
  
-   Если она выполняет несколько чувства упростить взаимодействие между DE и программой, то среду выполнения co\-создаст DE.  Это оставляет SDM в одно адресное пространство и DE, среду выполнения и в другие программы.  Обычно это DE, который реализуется с переводчиком для запуска языки, задействованные в сценариях.  
  
    > [!NOTE]
    >  Как DE вложение к программе реализация\-зависимая ячейка.  Взаимодействие между DE и программой также реализация\-зависимая ячейка.  
  
## Реализация  
 Программно, если сеанс отладки \(SDM\) сначала диспетчер возвращает [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) объект, который представляет программу, которую необходимо запускать, он вызывает  [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) метод, передав ему  [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) объект, который впоследствии используется для передачи события отладки назад к SDM.  Тогда метод `IDebugProgram2::Attach` вызывает метод [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md).  Дополнительные сведения о том, как SDM возвращает `IDebugProgram2` интерфейс см. в разделе  [Уведомление порт](../../extensibility/debugger/notifying-the-port.md).  
  
 Если DE необходимо выполнить в одном адресном пространстве, что отлаживаемый программу, как правило, это связано с тем, что часть преобразователя, выполняемых скриптов, DE `IDebugProgramNodeAttach2::OnAttach` метод возвращает  `S_FALSE`это означает, что он был запущен процесс вложить.  
  
 С другой стороны, если DE выполняется в адресном пространстве SDM, `IDebugProgramNodeAttach2::OnAttach` метод возвращает  `S_OK` или  [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) интерфейс не реализован во всех на  [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) объект, связанный с отлаживанными создаваемый программой.  В этом случае [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) метод наконец вызывается для выполнения операций присоединения.  
  
 В последнем случае необходимо вызвать [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) метод  `IDebugProgram2` объект, который был передан  `IDebugEngine2::Attach` метод сохраняет  `GUID` в локальном объекте, и верните это программы  `GUID` после  `IDebugProgram2::GetProgramId` затем вызывается метод для этого объекта.  `GUID` используется для указания программы уникальными на другое компоненты отладки.  
  
 Обратите внимание, что в случае `IDebugProgramNodeAttach2::OnAttach` возврат метода  `S_FALSE`"  `GUID` использование программы передается этому методу и оно  `IDebugProgramNodeAttach2::OnAttach` метод, устанавливающий  `GUID` на локальном объекте программы.  
  
 DE теперь вложен в программе и готов отправить все события запуска.  
  
## См. также  
 [Подключение к программе](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Уведомление порт](../../extensibility/debugger/notifying-the-port.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)