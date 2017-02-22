---
title: "PROCESS_INFO_FIELDS | Microsoft Docs"
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
  - "PROCESS_INFO_FIELDS"
helpviewer_keywords: 
  - "Перечисление PROCESS_INFO_FIELDS"
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# PROCESS_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Указывается, что тип сведений для извлечения процесса.  
  
## Синтаксис  
  
```cpp#  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```c#  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## Члены  
 PIF\_FILE\_NAME  
 Инициализируйте и использование `bstrFileName` поле   [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) структура.  
  
 PIF\_BASE\_NAME  
 Инициализируйте и использование `bstrBaseName` поле   `PROCESS_INFO` структура.  
  
 PIF\_TITLE  
 Инициализируйте и использование `bstrTitle` поле   `PROCESS_INFO` структура.  
  
 PIF\_PROCESS\_ID  
 Инициализируйте и использование `ProcessId` поле   `PROCESS_INFO` структура.  
  
 PIF\_SESSION\_ID  
 Инициализируйте и использование `dwSessionId` поле   `PROCESS_INFO` структура.  
  
 PIF\_ATTACHED\_SESSION\_NAME  
 Инициализируйте и использование `bstrAttachedSessionName` поле   `PROCESS_INFO` структура.  
  
 PIF\_CREATION\_TIME  
 Инициализируйте и использование `CreationTime` поле   `PROCESS_INFO` структура.  
  
 PIF\_FLAGS  
 Инициализируйте и использование `Flags` поле   `PROCESS_INFO` структура.  
  
 PIF\_ALL  
 Заполняет все поля.  
  
## Заметки  
 Передается методу [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) метод, чтобы показать, какие поля  [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) структура быть инициализированным.  
  
 Также используется в `Fields` поле   `PROCESS_INFO` структура для указания того, какие поля используются и допустимы.  
  
 Эти флаги могут объединяться с побитовый оператор `OR`.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)