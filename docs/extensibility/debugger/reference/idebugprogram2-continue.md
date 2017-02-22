---
title: "IDebugProgram2::Continue | Microsoft Docs"
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
  - "IDebugProgram2::Continue"
helpviewer_keywords: 
  - "IDebugProgram2::Continue"
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::Continue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Продолжает выполнять эту программу от остановленного состояния.  Сохраняется все предыдущее состояние выполнения \(в качестве шага\) и запуске программы при выполнении попытку.  
  
> [!NOTE]
>  Этот метод является устаревшим.  Взамен рекомендуется использовать метод [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md).  
  
## Синтаксис  
  
```cpp#  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```c#  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### Параметры  
 `pThread`  
 \[in\] IDebugThread2 объект, представляющий поток.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод вызывается в этой программе независимо от количества программ отладки или остановки программы, сформировавшего событие.  Реализация должна сохранять предыдущее состояние выполнения \(в качестве шага\) и возобновить выполнение, как если бы он не был остановлен перед выполнением ее прежнего выполнения.  То есть, если поток в этой программе внес a этап\-над операцией и был остановлен, поскольку другая определенная программа остановлена, а затем этот метод были вызваны, программа должна выполнить исходные этап\-над операцией.  
  
> [!WARNING]
>  Не отправить событие остановки или немедленно \(синхронный\), событие [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) хотя обработка этого вызова; в противном случае он может повиснуть.  
  
## См. также  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)