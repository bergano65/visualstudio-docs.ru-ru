---
title: "IDebugProcess3::Step | Microsoft Docs"
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
  - "IDebugProcess3::Step"
helpviewer_keywords: 
  - "IDebugProcess3::Step"
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::Step
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Вызывает процесс в инструкции или выписке раздела.  
  
> [!NOTE]
>  Этот метод следует использовать вместо [Шаг](../../../extensibility/debugger/reference/idebugprogram2-step.md).  
  
## Синтаксис  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```c#  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### Параметры  
 `pThread`  
 \[in\] IDebugThread2 объект, представляющий поток, шаганными.  
  
 `sk`  
 \[in\] одно из STEPKIND значения.  
  
 `step`  
 \[in\] одно из STEPUNIT значения.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 В случае если синхронизация потока или связь между потоками, другие потоки в процессе должны выполняться при шагает указанный поток.  
  
 **Предупреждение** Не отправить событие остановки или немедленно \(синхронный\), событие  [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) хотя обработка этого вызова; в противном случае он может повиснуть.  
  
## См. также  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)