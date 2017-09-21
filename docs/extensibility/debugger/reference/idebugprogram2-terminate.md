---
title: "IDebugProgram2::Terminate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Terminate"
helpviewer_keywords: 
  - "IDebugProgram2::Terminate"
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Завершает программу.  
  
## Синтаксис  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```c#  
int Terminate();  
```  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Если возможно, программа будет завершена и выгрузить из процесса; в противном случае, обработчик отладки \(DE\) выполняет любую необходимую очистку.  
  
 Этот метод или [Завершить](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) метод вызывается средой разработки, обычно в ответ на пользователь останавливая всю отладку.  Реализация этого метода должна быть завершена, в идеальном случае программа внутри процесса.  Если это невозможно, DE должен запретить программу выполнения более в этом процессе \(и выполнить любую необходимую очистку\).  Если `IDebugProcess2::Terminate` метод был вызван интегрированной средой разработки, весь процесс будет завершен когда\-то после  `IDebugProgram2::Terminate` вызывается метод.  
  
## См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Завершить](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)