---
title: "IDebugProgram2::GetDisassemblyStream | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetDisassemblyStream"
helpviewer_keywords: 
  - "IDebugProgram2::GetDisassemblyStream"
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgram2::GetDisassemblyStream
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Получает поток, дизассемблированный код для этой программы или часть этой программы.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetDisassemblyStream(   
   DISASSEMBLY_STREAM_SCOPE   dwScope,  
   IDebugCodeContext2*        pCodeContext,  
   IDebugDisassemblyStream2** ppDisassemblyStream  
);  
```  
  
```c#  
int GetDisassemblyStream(   
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,  
   IDebugCodeContext2             pCodeContext,  
   out IDebugDisassemblyStream2   ppDisassemblyStream  
);  
```  
  
#### Параметры  
 `dwScope`  
 \[in\] определяет значение [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) перечисление, определяющее область действия потока дизассемблированный код.  
  
 `pCodeContext`  
 \[in\] IDebugCodeContext2 объект, который представляет положение, где запуска потока дизассемблированный код.  
  
 `ppDisassemblyStream`  
 \[out\] возвращает [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) объект, представляющий поток, дизассемблированный код.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Возвращает `E_DISASM_NOTSUPPORTED` если дизассемблированный код не поддерживается для данной конкретной архитектуры.  
  
## Заметки  
 Если `dwScopes` параметр содержит  `DSS_HUGE` пометить  [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) предполагается, что возвращает набор перечисления, затем дизассемблирование большое количество инструкций дизассемблирования, например для всех файлов или модуля.  Если `DSS_HUGE` пометить не установлен, то предполагается, что дизассемблирование ограничивается к небольшой области, обычно этому одной функции.  
  
## См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)