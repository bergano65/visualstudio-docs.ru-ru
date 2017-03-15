---
title: "IDebugProcess2::CanDetach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::CanDetach"
helpviewer_keywords: 
  - "IDebugProcess2::CanDetach"
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::CanDetach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет, если сеанс отладки \(SDM\) и, наконец диспетчер может удалить процессы.  
  
## Синтаксис  
  
```cpp#  
HRESULT CanDetach(  
   void  
);  
```  
  
```c#  
int CanDetach();  
```  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK.` возвращает  `S_FALSE` если отладчик не может затем удалить из процесса.  В противном случае возвращает код ошибки.  
  
## См. также  
 [CanDetach](../Topic/IDebugProgram2::CanDetach.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)