---
title: "IDebugDisassemblyStream2::Read | Microsoft Docs"
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
  - "IDebugDisassemblyStream2::Read"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::Read"
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDisassemblyStream2::Read
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Считывает инструкцию, начиная с текущей позицией курсора в потоке дизассемблированный код.  
  
## Синтаксис  
  
```cpp#  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```c#  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### Параметры  
 `dwInstructions`  
 \[in\] количество инструкций демонтировать.  Это значение также максимальная длина  `prgDisassembly` массив.  
  
 `dwFields`  
 \[in\] сочетание пометит из [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) перечисление, указывающее которых полей  `prgDisassembly` быть заполнянным.  
  
 `pdwInstructionsRead`  
 \[out\] возвращает число фактически демонтированных инструкций.  
  
 `prgDisassembly`  
 \[out\] массив [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) структуры, который заполняется с демонтированным кодом, одна структура в демонтированную инструкцию.  Длина этого массива продиктована  `dwInstructions` параметр.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Максимальное количество инструкций, доступных в текущей области может быть получено вызовом [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) метод.  
  
 Текущая позиция, в которой считывается из следующая инструкция может быть изменено путем вызова [Поиск](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) метод.  
  
 `DSF_OPERANDS_SYMBOLS` пометить можно добавить к  `DSF_OPERANDS` пометить в  `dwFields` параметр для указания того, что имена символов должны использоваться демонтируя инструкции.  
  
## См. также  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [Поиск](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)