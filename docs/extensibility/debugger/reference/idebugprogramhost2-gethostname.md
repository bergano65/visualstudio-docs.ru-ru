---
title: "IDebugProgramHost2::GetHostName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramHost2::GetHostName"
helpviewer_keywords: 
  - "IDebugProgramHost2::GetHostName"
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает имя, понятное имя или имя файла ведущего процесса этой программы.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```c#  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### Параметры  
 `dwType`  
 \[in\] значение из [GETHOSTNAME\_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) перечисление.  
  
 `pbstrHostName`  
 \[out\] возвращает имя запрошенного ведущего процесса.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 В типичной реализации этого метода `dwType` параметр игнорируется, и является понятное имя компьютера\-узла.  Другая возможная реализация передачи `dwType` параметр к вызову  [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) метод, чтобы получить имя.  
  
## См. также  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)