---
title: "IDebugProcessEx2::Attach | Microsoft Docs"
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
  - "IDebugProcessEx2::Attach"
helpviewer_keywords: 
  - "Метод IDebugProcessEx2::Attach"
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessEx2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод сообщает, что сеанс теперь процесс отладки процесса.  
  
## Синтаксис  
  
```cpp#  
HRESULT Attach(   
   IDebugSession2* pSession  
);  
```  
  
```c#  
int Attach(  
   IDebugSession2 pSession  
);  
```  
  
#### Параметры  
 `pSession`  
 \[in\] значение, уникально определяющее сеанс вложа к данному процессу.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Интерфейс переданный `pSession` должна рассматриваться только как файл cookie, значение, уникально определяющее сеанс отладки диспетчер вложа к этому процессу; ни один из методов в интерфейсе, предоставляемом функциональны.  
  
## См. также  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)