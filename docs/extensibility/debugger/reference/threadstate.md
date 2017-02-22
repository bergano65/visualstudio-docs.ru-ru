---
title: "СОСТОЯНИЯ ПОТОКА | Microsoft Docs"
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
  - "THREADSTATE"
helpviewer_keywords: 
  - "Перечисление состояния ПОТОКА"
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# СОСТОЯНИЯ ПОТОКА
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Задает состояние потока.  
  
## Синтаксис  
  
```cpp#  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```c#  
public enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
```  
  
## Члены  
 THREADSTATE\_RUNNING  
 Указывает, что поток выполняется.  
  
 THREADSTATE\_STOPPED  
 Указывает, что поток остановлен из\-за точки останова.  
  
 THREADSTATE\_FRESH  
 Указывает, что был создан поток, но еще не выполняется код.  
  
 THREADSTATE\_DEAD  
 Указывает, что поток мертв.  
  
 THREADSTATE\_FROZEN  
 Указывает, что поток заморожен \(отсутствие выполнение может быть выполнена\).  
  
## Заметки  
 Используется для `dwThreadState` поле   [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) структура.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)