---
title: "IDebugProgramNodeAttach2::OnAttach | Microsoft Docs"
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
  - "IDebugProgramNodeAttach2::OnAttach"
helpviewer_keywords: 
  - "IDebugProgramNodeAttach2::OnAttach"
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Вложение в связанную программе или откладывает вложение в процесс [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод.  
  
## Синтаксис  
  
```cpp#  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```c#  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### Параметры  
 `guidProgramId`  
 \[in\] `GUID` присвоить связанной программе.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если  [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод не должен вызываться.  В противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод вызывается в процессе вложение, перед [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) вызывается метод.  `OnAttach` метод может выполнять вложение в процесс, который сам \(случае этот метод возвращает  `S_FALSE`обращаться\) или вложение в процесс  `IDebugEngine2::Attach` \(метод  `OnAttach` метод возвращает  `S_OK`\).  В любом событии `OnAttach` метод может задавать  `GUID` программы, отлаживанными с заданным  `GUID`.  
  
## См. также  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)