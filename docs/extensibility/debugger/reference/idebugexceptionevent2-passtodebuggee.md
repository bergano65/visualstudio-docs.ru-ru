---
title: "IDebugExceptionEvent2::PassToDebuggee | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2::PassToDebuggee"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::PassToDebuggee"
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет, должно ли исключение передается в отлаживаемом программе, когда выполнение возобновлении или если исключение должно отменено.  
  
## Синтаксис  
  
```cpp#  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```c#  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### Параметры  
 `fPass`  
 \[in\] ненулевое значение \(`TRUE`если исключение должно передается в отлаживаемом, то выполнение программы при возобновлении или нуль \(`FALSE`если исключение должно отменено.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Вызов этого метода фактически не будет выполняться в код отлаживаемой программы.  Вызов просто задать состояние для следующего выполнения кода.  Например, вызовы [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) метод может возвратить  `S_OK` с  [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` набор полей  `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 Интегрированная среда разработки может получать [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) событие и вызывает  [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md) метод.  Отладчик \(DE\) должен иметь по умолчанию расширение функциональности для обработки случае, если `PassToDebuggee` метод не вызывается.  
  
## См. также  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)