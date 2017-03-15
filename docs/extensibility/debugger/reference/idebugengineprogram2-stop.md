---
title: "IDebugEngineProgram2::Stop | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::Stop"
helpviewer_keywords: 
  - "IDebugEngineProgram2::Stop"
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugEngineProgram2::Stop
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Останавливает все потоки в этой программе.  
  
## Синтаксис  
  
```cpp#  
HRESULT Stop(   
   void   
);  
```  
  
```c#  
int Stop();  
```  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод вызывается, когда эта программа отладки среды multi\-программы.  Когда событие получено при остановке из какой\-либо другой программы, этот метод вызывается в этой программе.  Реализация этого метода должна быть является асинхронной; это значит, что не все потоки должны необходимо, чтобы были остановлены, прежде чем этот метод возвращает значения.  Реализация этого метода может быть как простой как вызов [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) метод в этой программе.  
  
 Нет отладка событие отправляет в ответ на этот метод.  
  
## См. также  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)