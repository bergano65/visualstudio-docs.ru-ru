---
title: "IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs"
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
  - "IDebugProcessEx2::AddImplicitProgramNodes"
helpviewer_keywords: 
  - "Метод IDebugProcessEx2::AddImplicitProgramNodes"
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод добавляет узел программы для каждого указанный обработчик отладки \(DE\).  
  
## Синтаксис  
  
```cpp#  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```c#  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### Параметры  
 `guidLaunchingEngine`  
 \[in\] `GUID` DE, для использования запуск программы \(и предполагает, что добавить собственные узлы программы\).  
  
 `rgguidSpecificEngines`  
 \[in\] массив `GUID`s DEs, для которого узлы программы будут добавлены.  
  
 `celtSpecificEngines`  
 \[in\] число `GUID`в  `rgguidSpecificEngines` массив.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 [Программа узлов](../../../extensibility/debugger/program-nodes.md) добавляет для каждого перечисляемого внутри DE `rgguidSpecificEngines`\- за исключением начальной обработчика \(например, уступано  `guidLaunchingEngine`\), который предполагается, что добавляет собственный узел программы, когда он запускает программу.  
  
## См. также  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Программа узлов](../../../extensibility/debugger/program-nodes.md)