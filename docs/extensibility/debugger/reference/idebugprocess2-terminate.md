---
title: "IDebugProcess2::Terminate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::Terminate"
helpviewer_keywords: 
  - "IDebugProcess2::Terminate"
ms.assetid: 5e6bf373-0fe9-4321-b04a-473a65f664d9
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::Terminate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Завершает процесс.  
  
## Синтаксис  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```c#  
int Terminate();  
```  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Если процесс завершен все программы в рамках этого процесса завершенны; нет допускаются выполнять больше кода.  
  
## См. также  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)