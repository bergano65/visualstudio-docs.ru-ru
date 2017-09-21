---
title: "IDebugDisassemblyStream2::GetCodeContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::GetCodeContext"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::GetCodeContext"
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::GetCodeContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает объект контекста кода, соответствующее указанному идентификатору расположение кода.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetCodeContext(   
   UINT64               uCodeLocationId,  
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```c#  
int GetCodeContext(   
   ulong                  uCodeLocationId,  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### Параметры  
 `uCodeLocationId`  
 \[in\] определяет идентификатор расположение кода.  См. раздел " примечания ", [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md) метод описание идентификатора расположение кода.  
  
 `ppCodeContext`  
 \[out\] возвращает IDebugCodeContext2 объект, представляющий связанный контекст кода.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Идентификатор расположение кода можно возвратить в результате вызова [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md) метод и может появляться в  [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) структура.  
  
 Чтобы преобразовать идентификатор контекста кода в расположение кода, вызовите [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md) метод.  
  
## См. также  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)   
 [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)