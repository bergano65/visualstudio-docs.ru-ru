---
title: "IDebugProgram2::Step | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Step"
helpviewer_keywords: 
  - "IDebugProgram2::Step"
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Выполняет шаг.  
  
> [!NOTE]
>  Этот метод является устаревшим.  Взамен рекомендуется использовать метод [Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## Синтаксис  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```c#  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### Параметры  
 `pThread`  
 \[in\] IDebugThread2 объект, представляющий поток, шаганным.  
  
 `sk`  
 \[in\] значение из STEPKIND перечисление, определяющее тип шага.  
  
 `step`  
 \[in\] значение из STEPUNIT перечисление, которое определяет единицу измерения этапа \(например, выпиской или инструкцией\).  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 В случае если синхронизация потока или связь между потоками, другие потоки в программе должен выполняться, когда указанный поток шагает.  
  
> [!WARNING]
>  Не отправить событие остановки или немедленно \(синхронный\), событие [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) хотя обработка этого вызова; в противном случае он может повиснуть.  
  
## См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)