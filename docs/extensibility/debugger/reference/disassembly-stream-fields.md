---
title: DISASSEMBLY_STREAM_FIELDS | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a8735992574699ba2b108fc493e9003ca52c9b2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
Указывает, какую информацию для получения по полю Дизассемблированный код.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
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
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
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
  
## <a name="members"></a>Участники  
 DSF_ADDRESS  
 Инициализация или использовать `bstrAddress` поле.  
  
 DSF_ADDRESSOFFSET  
 Инициализация или использовать `bstrAddressOffset` поле.  
  
 DSF_CODEBYTES  
 Инициализация или использовать `bstrCodeBytes` поле.  
  
 DSF_OPCODE  
 Инициализация или использовать `bstrOpCode` поле.  
  
 DSF_OPERANDS  
 Инициализация или использовать `bstrOperands` поле.  
  
 DSF_SYMBOL  
 Инициализация или использовать `bstrSymbol` поле.  
  
 DSF_CODELOCATIONID  
 Инициализация или использовать `uCodeLocationId` поле.  
  
 DSF_POSITION  
 Инициализация или использовать `posBeg` и `posEnd` поля.  
  
 DSF_DOCUMENTURL  
 Инициализация или использовать `bstrDocumentUrl` поле.  
  
 DSF_BYTEOFFSET  
 Инициализация или использовать `dwByteOffset` поле.  
  
 DSF_FLAGS  
 Инициализация или использовать `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) поля.  
  
 DSF_OPERANDS_SYMBOLS  
 Включить имена символов в `bstrOperands` поле.  
  
 DSF_ALL  
 Указывает все поля для потока Дизассемблированный код.  
  
## <a name="remarks"></a>Примечания  
 Переданное в качестве параметра для [чтения](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) метод, чтобы указать, какие поля [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) структуры должны быть инициализированы.  
  
 Используется для `dwFields` членом `DisassemblyData` структуры указывает, какие поля используются и допустимым при возврате структуры.  
  
 Эти значения могут объединяться с помощью битового оператора `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Чтение](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)