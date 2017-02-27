---
title: "DISASSEMBLY_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_FLAGS"
helpviewer_keywords: 
  - "Перечисление DISASSEMBLY_FLAGS"
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Указывает флаги для дизассемблирования.  
  
## Синтаксис  
  
```cpp#  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```c#  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## Члены  
 DF\_DOCUMENTCHANGE  
 Указывает, что эта инструкция в другом документе, чем предыдущий.  
  
 DF\_DISABLED  
 Указывает, что эта инструкция не будет выполнена.  
  
 DF\_INSTRUCTION\_ACTIVE  
 Указывает, что эта инструкция одной из следующих инструкций для выполнения \(часть сообщения может встречаться в сообщении несколько\).  
  
 DF\_DATA  
 Указывает, что эта инструкция не являются данные \(код\).  
  
 DF\_HASSOURCE  
 Указывает, что эта инструкция имеет источник.  Некоторые инструкции, как профилирование или код сборки мусора, не имеет соответствующего источника.  
  
 DF\_DOCUMENT\_CHECKSUM  
 Указывает, что `bstrDocumentUrl` поле содержит сведения о контрольной сумме выберите URL\-адрес документа.  См. раздел " примечания ", [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) структура, например сведения о контрольной сумме сохраняются.  
  
## Заметки  
 Используется как `dwFlags` элемент  [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) структура.  
  
 Эти флаги могут объединяться с побитовый оператор `OR`.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)