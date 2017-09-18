---
title: "PROCESS_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROCESS_INFO_FLAGS"
helpviewer_keywords: 
  - "Перечисление PROCESS_INFO_FLAGS"
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Описывает или задает свойства процесса.  
  
## Синтаксис  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```c#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## Члены  
 PIFLAG\_SYSTEM\_PROCESS  
 Указывает, что процесс процесс системы.  
  
 PIFLAG\_DEBUGGER\_ATTACHED  
 Указывает, что процесс отладки отладчиком.  Это может быть a [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] отладчик или другой отладчиком, например WinDbg.  
  
 PIFLAG\_PROCESS\_STOPPED  
 Указывает, что процесс завершается.  Допустимо, только если `PIFLAG_DEBUGGER_ATTACHED` также указывает.  Доступный внутри [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] и более поздних версиях.  
  
 PIFLAG\_PROCESS\_RUNNING  
 Указывает, что процесс запущен.  Допустимо, только если `PIFLAG_DEBUGGER_ATTACHED` также указывает.  Доступный внутри [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] и более поздних версиях.  
  
## Заметки  
 Используется для `Flags` элемент  [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) структура.  
  
 Эти флаги могут объединяться с побитовый оператор `OR`.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)