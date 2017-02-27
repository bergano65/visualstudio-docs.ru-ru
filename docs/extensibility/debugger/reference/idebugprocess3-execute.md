---
title: "IDebugProcess3::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::Execute"
helpviewer_keywords: 
  - "IDebugProcess3::Execute"
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess3::Execute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Выполнение продолжает этот процесс от остановленного состояния.  Очищено любое предыдущее состояние выполнения \(в качестве шага\) и запуске процесса выполнения.  
  
> [!NOTE]
>  Этот метод следует использовать вместо [Выполнение](../../../extensibility/debugger/reference/idebugprogram2-execute.md).  
  
## Синтаксис  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```c#  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### Параметры  
 `pThread`  
 \[in\] IDebugThread2 объект, представляющий поток для выполнения.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Когда пользователь запускает выполнение из остановленного состояния в потоке другого процесса этот метод вызывается при этом процессе.  Этот метод также вызывается, когда пользователь выбирает **Запуск** команда из  **Отладка** меню " в интегрированной среде разработки.  Реализация этого метода может быть как простой как вызов [Возобновить](../../../extensibility/debugger/reference/idebugthread2-resume.md) метод на текущем потоке в процессе.  
  
> [!WARNING]
>  Не отправить событие остановки или немедленно \(синхронный\), событие [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) хотя обработка этого вызова; в противном случае он может повиснуть.  
  
## См. также  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Возобновить](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)