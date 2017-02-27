---
title: "IDebugEngine3::SetJustMyCodeState | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::SetJustMyCodeState"
helpviewer_keywords: 
  - "IDebugEngine3::SetJustMyCodeState"
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод сообщает отладчик о JustMyCode сведений о состоянии.  
  
## Синтаксис  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```c#  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### Параметры  
 `fUpdate`  
 \[in\] ненулевое значение \(`TRUE`\), ноль \(обновлять текущие сведения`FALSE`сбросить все сведения \(\) ничего игнорируя ранее задано\).  
  
 `dwModules`  
 \[in\] количество структур данных в `rgJMCSpec.`  
  
 `rgJMCSpec`  
 \[in\] массив [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) структуры следует использовать.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 JustMyCode понятие отладки только код, который принадлежит пользователю и игнорировать все промежуточный код, как система код\-ровная если исходный код доступен для системного кода.  
  
## См. также  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)