---
title: "IDebugPortNotify2::RemoveProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortNotify2::RemoveProgramNode"
helpviewer_keywords: 
  - "IDebugPortNotify2::RemoveProgramNode"
ms.assetid: 3668157b-66d2-416e-a359-fc04dcd18a48
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortNotify2::RemoveProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Отменяет регистрацию программа, можно отлаживать от порта он запущен.  
  
## Синтаксис  
  
```cpp#  
HRESULT RemoveProgramNode(   
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```c#  
int RemoveProgramNode(   
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### Параметры  
 `pProgramNode`  
 \[in\] IDebugProgramNode2 objecy, которое представляет собой программу на незарегистрированно.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод удаляет узел программы, который был добавлен, вызвав [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) метод.  
  
## См. также  
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)