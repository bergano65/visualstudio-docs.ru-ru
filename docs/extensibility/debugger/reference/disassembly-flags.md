---
title: DISASSEMBLY_FLAGS | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd1aa9c73fad40d07be371ad7f9b3108464aeb34
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
Задает флаги для дизассемблирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>Участники  
 DF_DOCUMENTCHANGE  
 Указывает, что эта инструкция является в другом документе, чем предыдущая.  
  
 DF_DISABLED  
 Указывает, что эта инструкция не будет выполняться.  
  
 DF_INSTRUCTION_ACTIVE  
 Указывает, что эта инструкция является один далее инструкциям для выполнения (может быть несколько).  
  
 DF_DATA  
 Указывает, эта инструкция является данных (не код).  
  
 DF_HASSOURCE  
 Указывает, что эта инструкция имеет источника. Некоторые инструкции, например, профилирование и сборке мусора код коллекции имеют нет соответствующего источника.  
  
 DF_DOCUMENT_CHECKSUM  
 Указывает, что `bstrDocumentUrl` поле содержит данных контрольной суммы после URL-адрес документа. В разделе «Примечания» [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) структуру для способ хранения данных контрольной суммы.  
  
## <a name="remarks"></a>Примечания  
 Используется в качестве `dwFlags` членом [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) структуры.  
  
 Эти флаги могут объединяться с битовой `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)