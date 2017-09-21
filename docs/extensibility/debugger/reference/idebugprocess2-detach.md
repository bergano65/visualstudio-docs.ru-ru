---
title: "IDebugProcess2::Detach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::Detach"
helpviewer_keywords: 
  - "IDebugProcess2::Detach"
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::Detach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Наконец удаляет отладчик из данного процесса, наконец удалить все программы в процессе.  
  
## Синтаксис  
  
```cpp#  
HRESULT Detach(   
   void   
);  
```  
  
```c#  
int Detach();  
```  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Все программы и процесс продолжают выполняться, но больше не является частью сеанса отладки.  После завершения операции наконец удаления не больше не отладочные события для этого процесса \(и его программ\) будут отправлены.  
  
## См. также  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)