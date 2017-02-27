---
title: "IDebugProgram3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugProgram3"
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugProgram3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет программу, которая выполняется в процессе и расширяет [Выполнение](../../../extensibility/debugger/reference/idebugprogram2-execute.md) предоставляя сведения о потоке.  
  
## Синтаксис  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) и пользовательского поставщика порта реализуйте этот интерфейс для представления программу в процессе.  Сеанс отладки \(SDM\) диспетчер также реализует этот интерфейс, чтобы предоставить сведения [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## Замечания для вызывающих объектов  
 IDebugProgramCreateEvent2 событие возвращает этот интерфейс для новой программы.  Этот интерфейс также используется в качестве параметра для многих методов на нескольких интерфейсах.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugProgram3`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Выполняет программу.  Поток возвращается для предоставления сведений отладчика, на которых поток пользователь просматривает при выполнении.|  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Заметки  
 Программа работы контейнера потока в заданной архитектуры среды выполнения, пока процесс состоит из одного или нескольких программ.  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../Topic/IDebugThread2::GetProgram.md)   
 [Далее](../Topic/IEnumDebugPrograms2::Next.md)   
 [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)