---
title: "DISASSEMBLY_STREAM_FIELDS | Microsoft Docs"
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
  - "DISASSEMBLY_STREAM_FIELDS"
helpviewer_keywords: 
  - "Перечисление DISASSEMBLY_STREAM_FIELDS"
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# DISASSEMBLY_STREAM_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Указывает, какую информацию, которую необходимо извлечь о поле дизассемблированный код.  
  
## Синтаксис  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
typedef DWORD DISASSEMBLY_STREAM_FIELDS;  
```  
  
```c#  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
```  
  
## Члены  
 DSF\_ADDRESS  
 Инициализируйте и использование `bstrAddress` поле.  
  
 DSF\_ADDRESSOFFSET  
 Инициализируйте и использование `bstrAddressOffset` поле.  
  
 DSF\_CODEBYTES  
 Инициализируйте и использование `bstrCodeBytes` поле.  
  
 DSF\_OPCODE  
 Инициализируйте и использование `bstrOpCode` поле.  
  
 DSF\_OPERANDS  
 Инициализируйте и использование `bstrOperands` поле.  
  
 DSF\_SYMBOL  
 Инициализируйте и использование `bstrSymbol` поле.  
  
 DSF\_CODELOCATIONID  
 Инициализируйте и использование `uCodeLocationId` поле.  
  
 DSF\_POSITION  
 Инициализируйте и использование `posBeg` и  `posEnd` поля.  
  
 DSF\_DOCUMENTURL  
 Инициализируйте и использование `bstrDocumentUrl` поле.  
  
 DSF\_BYTEOFFSET  
 Инициализируйте и использование `dwByteOffset` поле.  
  
 DSF\_FLAGS  
 Инициализируйте и использование `dwFlags` \([DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)поле\).  
  
 DSF\_OPERANDS\_SYMBOLS  
 Включить имена символов в `bstrOperands` поле.  
  
 DSF\_ALL  
 Указывает все поля для потока дизассемблированный код.  
  
## Заметки  
 Передается как параметр [Чтение](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) метод, чтобы показать, какие поля  [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) структура быть инициализированным.  
  
 Используется для `dwFields` элемент  `DisassemblyData` структура, чтобы показать, какие поля используются и допустимы, если структура возвращается.  
  
 Эти значения могут объединяться с побитовый оператор `OR`.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Чтение](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)