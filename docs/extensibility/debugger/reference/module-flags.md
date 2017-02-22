---
title: "MODULE_FLAGS | Microsoft Docs"
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
  - "MODULE_FLAGS"
helpviewer_keywords: 
  - "Перечисление MODULE_FLAGS"
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# MODULE_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Используется для описания модуль.  
  
## Синтаксис  
  
```cpp#  
enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
typedef DWORD MODULE_FLAGS;  
```  
  
```c#  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## Члены  
 MODULE\_FLAG\_NONE  
 Не задает ни один модуль.  
  
 MODULE\_FLAG\_SYSTEM  
 Определяет модуль системы.  
  
 MODULE\_FLAG\_SYMBOLS  
 Определяет модуль символов.  
  
 MODULE\_FLAG\_64BIT  
 Определяет 64 модуль.  
  
 MODULE\_FLAG\_OPTIMIZED  
 Позволяет оптимизировать определяющую модуль.  Это состояние отражается в **Модули** окна.  
  
 MODULE\_FLAG\_UNOPTIMIZED  
 Определяет модуль не позволяет оптимизировать.  Это состояние отражается в **Модули** окна.  Это состояние по умолчанию.  
  
## Заметки  
 Используется для `m_dwModuleFlags` элемент  [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) структура.  
  
 Эти флаги могут объединяться с побитовый оператор `OR`.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)