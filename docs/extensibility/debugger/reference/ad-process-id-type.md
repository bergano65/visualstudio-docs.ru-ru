---
title: "AD_PROCESS_ID_TYPE | Microsoft Docs"
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
  - "AD_PROCESS_ID_TYPE"
helpviewer_keywords: 
  - "Перечисление AD_PROCESS_ID_TYPE"
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет способ интерпретации идентификатор процесса в [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) структура.  
  
## Синтаксис  
  
```cpp#  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```c#  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## Члены  
 AD\_PROCESS\_ID\_SYSTEM  
 Идентификатор процесса идентификатор системы.  Используйте `ProcessId.dwProcessId` поле   [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) структура.  
  
 AD\_PROCESS\_ID\_GUID  
 Идентификатор процесса GUID.  Используйте `ProcessId.guidProcessId` поле   `AD_PROCESS_ID` структура.  
  
## Заметки  
 Используется для `ProcessIdType` элемент  [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) структура для указания типа процесса, которая содержится в структуре.  Определяет, как интерпретировать `ProcessId` объединение в структуре.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)