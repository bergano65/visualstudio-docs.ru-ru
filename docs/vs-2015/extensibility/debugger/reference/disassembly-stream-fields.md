---
title: DISASSEMBLY_STREAM_FIELDS | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1b5c0b3f06299f9f78a6f24d8c25410a9eb4a9ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569067"
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [DISASSEMBLY_STREAM_FIELDS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/disassembly-stream-fields).  
  
Указывает, какую информацию нужно извлечь по полю Дизассемблированный код.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Инициализация и использование `bstrAddress` поля.  
  
 DSF_ADDRESSOFFSET  
 Инициализация и использование `bstrAddressOffset` поля.  
  
 DSF_CODEBYTES  
 Инициализация и использование `bstrCodeBytes` поля.  
  
 DSF_OPCODE  
 Инициализация и использование `bstrOpCode` поля.  
  
 DSF_OPERANDS  
 Инициализация и использование `bstrOperands` поля.  
  
 DSF_SYMBOL  
 Инициализация и использование `bstrSymbol` поля.  
  
 DSF_CODELOCATIONID  
 Инициализация и использование `uCodeLocationId` поля.  
  
 DSF_POSITION  
 Инициализация и использование `posBeg` и `posEnd` поля.  
  
 DSF_DOCUMENTURL  
 Инициализация и использование `bstrDocumentUrl` поля.  
  
 DSF_BYTEOFFSET  
 Инициализация и использование `dwByteOffset` поля.  
  
 DSF_FLAGS  
 Инициализация и использование `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) поля.  
  
 DSF_OPERANDS_SYMBOLS  
 Включить имена символов в `bstrOperands` поля.  
  
 DSF_ALL  
 Указывает все поля для потока Дизассемблированный код.  
  
## <a name="remarks"></a>Примечания  
 Переданный в качестве параметра для [чтения](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) метод, чтобы указать, какие поля [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) структуры должны быть инициализированы.  
  
 Используется для `dwFields` членом `DisassemblyData` структура указывает, какие поля используются и допустимым при возвращении структуры.  
  
 Эти значения могут объединяться с побитовым объектом `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Чтение](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)

