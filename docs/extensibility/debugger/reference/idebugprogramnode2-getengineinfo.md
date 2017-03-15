---
title: "IDebugProgramNode2::GetEngineInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::GetEngineInfo"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetEngineInfo"
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramNode2::GetEngineInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Получает имя обработчика отладки и идентификатор \(DE\) при запуске программы.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetEngineInfo (   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```c#  
int GetEngineInfo(  
   out string pbstrEngine,   
   out Guid pguidEngine  
);  
```  
  
#### Параметры  
 `pbstrEngine`  
 \[out\] возвращает имя выполняющегося программы \(C\+\+\-specific: DE это может быть пустым указателем, указывающий на то, что участник не нужны маркетинговые данные из имени обработчика\).  
  
 `pguidEngine`  
 \[out\] возвращает глобальный уникальный идентификатор выполняющегося программы \(C\+\+\-specific: DE это может быть пустым указателем, указывающий на то, что участник не нужны маркетинговые данные в GUID обработчика\).  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)