---
title: "IDebugProgramNode2::GetHostPid | Microsoft Docs"
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
  - "IDebugProgramNode2::GetHostPid"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetHostPid"
ms.assetid: e65b4b15-46d8-4ca7-9456-2b4c078f7cf9
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNode2::GetHostPid
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает идентификатор системного процесса для процесса размещения программы.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetHostPid (   
   AD_PROCESS_ID * pdwHostPid  
);  
```  
  
```c#  
int GetHostPid (   
   out AD_PROCESS_ID pdwHostPid  
);  
```  
  
#### Параметры  
 `pdwHostPid`  
 \[out\] возвращает идентификатор системного процесса для ведущего процесса.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Пример  
 В следующем примере показано, как реализовать этот метод для простого `CProgram` объект, реализующий  [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейс.  
  
```cpp#  
HRESULT CProgram::GetHostPid(DWORD* pdwHostPid) {    
    // Check for valid argument.    
   if (pdwHostPid)    
    {    
        // Get the process identifier of the calling process.    
      *pdwHostPid = GetCurrentProcessId();    
  
        return S_OK;    
    }    
  
    return E_INVALIDARG;    
}    
```  
  
## См. также  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)