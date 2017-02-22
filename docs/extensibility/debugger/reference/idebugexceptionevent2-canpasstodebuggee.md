---
title: "IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs"
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
  - "IDebugExceptionEvent2::CanPassToDebuggee"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::CanPassToDebuggee"
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет, поддерживает ли отладчик \(DE\) параметр передача это исключение в отлаживанными программе, когда выполнение продолжится.  
  
## Синтаксис  
  
```cpp#  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```c#  
int CanPassToDebuggee();  
```  
  
## Возвращаемое значение  
 Возвращает значение `S_OK` \(исключение может быть передано в программе\) или  `S_FALSE` \(исключение \- невозможно передать on\).  
  
## Заметки  
 DE должен быть действие по умолчанию для передачи в отлаживаемый процесс.  Интегрированная среда разработки может получать [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) событие и вызывает  [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) метод без вызова  `CanPassToDebuggee` метод.  Поэтому DE должен иметь аргументы по умолчанию, передав исключение on.  
  
## См. также  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)