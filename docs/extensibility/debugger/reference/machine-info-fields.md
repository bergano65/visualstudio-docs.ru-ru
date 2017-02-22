---
title: "MACHINE_INFO_FIELDS | Microsoft Docs"
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
  - "MACHINE_INFO_FIELDS"
helpviewer_keywords: 
  - "Перечисление MACHINE_INFO_FIELDS"
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# MACHINE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет, какие сведения, которые необходимо получить для указанного компьютера.  
  
## Синтаксис  
  
```cpp#  
enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
typedef DWORD MACHINE_INFO_FIELDS;  
```  
  
```c#  
public enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
```  
  
## Члены  
 MCIF\_NAME  
 Инициализируйте и использование `bstrName` поля в макете.  
  
 MCIF\_FLAGS  
 Инициализируйте и использование `Flags` поля в макете.  
  
 MIF\_ALL  
 Инициализируйте и использование все поля в макете.  
  
## Заметки  
 Эти значения передаются [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md) метод, чтобы показать, какие элементы  [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md) структура быть инициализированным.  
  
 Также используется в `Fields` элемент  `MACHINE_INFO` структура для указания того, какие поля используются и допустимы.  
  
 Эти флаги могут объединяться с побитовый оператор `OR`.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md)