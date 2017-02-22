---
title: "IDebugThread2::Resume | Microsoft Docs"
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
  - "IDebugThread2::Resume"
helpviewer_keywords: 
  - "IDebugThread2::Resume"
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возобновляет выполнение потока.  
  
## Синтаксис  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```c#  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### Параметры  
 `pdwSuspendCount`  
 \[out\] возвращает счетчик приостановки после операции восстановления.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Каждый вызов этого метода уменьшает количество приостанавливается до тех пор, пока он не достигнет 0, в который фактически возобновление время выполнения.  Это число отображается в suspend **потоки** окна отладки.  
  
 Для каждого вызова этого метода, должен быть предыдущий вызов [Suspend](../Topic/IDebugThread2::Suspend.md) метод.  Количество приостановить указывающее, сколько раз `IDebugThread2::Suspend` метод вызван на данный момент.  
  
## См. также  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../Topic/IDebugThread2::Suspend.md)