---
title: "IDebugProcessEx2::Detach | Microsoft Docs"
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
  - "IDebugProcessEx2::Detach"
helpviewer_keywords: 
  - "Метод IDebugProcessEx2::Detach"
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessEx2::Detach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод сообщает процессу, что сеанс не процесс отладки.  
  
## Синтаксис  
  
```cpp#  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```c#  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### Параметры  
 `pSession`  
 \[in\] значение, уникально определяющее сеанс, чтобы в итоге удалить этот процесс.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Интерфейс переданный `pSession` должна рассматриваться только как файл cookie, значение, уникально определяющее сеанс отладки диспетчер, который изначально вложил к этому процессу; ни один из методов в интерфейсе, предоставляемом функциональны.  
  
## См. также  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)