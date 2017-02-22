---
title: "DEBUG_REASON | Microsoft Docs"
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
  - "DEBUG_REASON"
helpviewer_keywords: 
  - "Перечисление DEBUG_REASON"
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUG_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Указывает причину, по которой был запущен процесс отладки.  
  
## Синтаксис  
  
```cpp#  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```c#  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### Параметры  
 DEBUG\_REASON\_ERROR  
 Неспецифичная произошла ошибка \(это значение используется как условие по умолчанию, если ни одна из других причин соответствия\).  
  
 DEBUG\_REASON\_USER\_LAUNCHED  
 Процесс запущен по запроса пользователя.  
  
 DEBUG\_REASON\_USER\_ATTACHED  
 Процесс уже\-хода был вложен пользователю.  
  
 DEBUG\_REASON\_AUTO\_ATTACHED  
 Процесс был вложен в автоматически, когда он запущен.  
  
 DEBUG\_REASON\_CAUSALITY  
 Процесса запущено из\-за a *Jit\-отладка* \(JIT\), событие отладки.  
  
## Заметки  
 Возвращает [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) метод.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)