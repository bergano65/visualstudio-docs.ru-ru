---
title: "SEEK_START | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SEEK_START"
helpviewer_keywords: 
  - "Перечисление SEEK_START"
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# SEEK_START
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Задает положение, с которого следует начать поиск в потоке дизассемблированный код.  
  
## Синтаксис  
  
```cpp#  
enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
typedef DWORD SEEK_START;  
```  
  
```c#  
public enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
```  
  
## Члены  
 SEEK\_START\_BEGIN  
 Начинает поиск в начале текущего документа.  
  
 SEEK\_START\_END  
 Начинает поиск в конце текущего документа.  
  
 SEEK\_START\_CURRENT  
 Начинает поиск в текущей позиции текущего документа.  
  
 SEEK\_START\_CODECONTEXT  
 Начинает иская в заданном контексте кода текущего документа.  
  
 SEEK\_START\_CODELOCID  
 Начинает иская на заданном идентификаторе расположение кода.  Идентификаторы расположение кода получены путем вызова [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md).  
  
## Заметки  
 Передается в качестве аргумента [Поиск](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) метод.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Поиск](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)   
 [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)