---
title: "IDebugEngineProgram2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2"
helpviewer_keywords: 
  - "Интерфейс IDebugEngineProgram2"
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEngineProgram2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс предоставляет multi\-продетую потоками поддержку отладки.  
  
## Синтаксис  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик реализующий этот интерфейс, чтобы поддерживать синхронную отладку нескольких потоков.  Этот интерфейс реализуется для одного и того же объекта, реализующего IDebugProgram2 интерфейс.  
  
## Замечания для вызывающих объектов  
 Используйте [QueryInterface](/visual-cpp/atl/queryinterface) получить этот интерфейс с  `IDebugProgram2` интерфейс.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugEngineProgram2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Останавливает все потоки в этой программе.|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Следит для выполнения \(или остановки следя для выполнения\) в данном потоке.|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Разрешает или запрещает\) вычисление выражений в данном потоке, даже если программа остановлена.|  
  
## Заметки  
 Visual Studio вызывает этот интерфейс в ответ на IDebugProgramCreateEvent2 событие и установить для шага потока "контрольные значения" и "контрольные значения для вычисления выражений в потоке" состояние программы.  [Остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) вызывается, когда программа быть остановки; этот метод дает программе возможность завершить все потоки.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)