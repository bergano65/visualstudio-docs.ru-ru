---
title: "IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::WatchForThreadStep"
helpviewer_keywords: 
  - "IDebugEngineProgram2::WatchForThreadStep"
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugEngineProgram2::WatchForThreadStep
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Следит для выполнения \(или останавливает контрольных для выполнения\) в данном потоке.  
  
## Синтаксис  
  
```cpp#  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```c#  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### Параметры  
 `pOriginatingProgram`  
 \[in\] IDebugProgram2 объект, представляющий шаганным, utility.  
  
 `dwTid`  
 \[in\] определяет идентификатор потока для контрольных.  
  
 `fWatch`  
 \[in\] ненулевое значение \(`TRUE`\) означает начало следя для выполнения в потоке, указанном контекстом by  `dwTid`; в противном случае \- нуль \(`FALSE`\) означает остановить следя для выполнения on  `dwTid`.  
  
 `dwFrame`  
 \[in\] определяет индекс кадра, который управляет тип шага.  Если это значение равно нулю \(0\), тип этого этапа "шаг с заходом" и программа должна прекращать, когда поток указанный by `dwTid` выполнить.  После `dwFrame` тип шага безнулева, "шаг" и над программа должна прекращать, только если поток указанный by  `dwTid` выполняема во фрейме индекс которого равен или более высоком уровне в стеке, чем  `dwFrame`.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Когда сеанс отладки действия диспетчера \(SDM\) программа, указанная `pOriginatingProgram` параметр, он уведомляет все другие вложенные программы, вызвав этот метод.  
  
 Этот метод применим только для пошаговой так же\-потока.  
  
## См. также  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)