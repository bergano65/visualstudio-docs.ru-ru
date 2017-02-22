---
title: "IDebugProcess3::Continue | Microsoft Docs"
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
  - "IDebugProcess3::Continue"
helpviewer_keywords: 
  - "IDebugProcess3::Continue"
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::Continue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Выполнение продолжает этот процесс от остановленного состояния.  Сохраняется все предыдущее состояние выполнения \(в качестве шага\) и начинается при выполнении процесса.  
  
> [!NOTE]
>  Этот метод следует использовать вместо [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
## Синтаксис  
  
```cpp  
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
 \[in\] IDebugThread2 объект, представляющий поток, который следует продолжить.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод вызывается в процессе независимо от количества процесса отладки или остановки процесса создавший событие.  Реализация должна сохранять предыдущее состояние выполнения \(в качестве шага\) и возобновить выполнение, как если бы он не был остановлен перед выполнением ее прежнего выполнения.  То есть, если поток в этом процессе внес a этап\-над операцией и был остановлен, поскольку какой\-либо другой процесс остановлен, а затем `Continue` вызова, заданный поток завершает исходный этап\-над операцией.  
  
 **Предупреждение** Не отправить событие остановки или немедленно \(синхронный\), событие  [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) хотя обработка этого вызова; в противном случае он может повиснуть.  
  
## См. также  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)