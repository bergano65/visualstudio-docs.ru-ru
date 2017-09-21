---
title: "THREADPROPERTY_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "THREADPROPERTY_FIELDS"
helpviewer_keywords: 
  - "Перечисление THREADPROPERTY_FIELDS"
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет, какие сведения о потоке требуется извлечь.  
  
## Синтаксис  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```c#  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## Члены  
 TPF\_ID  
 Инициализируйте и использование `dwThreadId` поле   [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) структура.  
  
 TPF\_SUSPENDCOUNT  
 Инициализируйте и использование `dwSuspendCount` поле   `THREADPROPERTIE`структура s.  
  
 TPF\_STATE  
 Инициализируйте и использование `dwThreadState` поле   `THREADPROPERTIE`структура s.  
  
 TPF\_PRIORITY  
 Инициализируйте и использование `bstrPriority` поле   `THREADPROPERTIE`структура s.  
  
 TPF\_NAME  
 Инициализируйте и использование `bstrName` поле   `THREADPROPERTIE`структура s.  
  
 TPF\_LOCATION  
 Инициализируйте и использование `bstrLocation` поле   `THREADPROPERTIE`структура s.  
  
 TPF\_ALLFIELDS  
 Указывает все поля.  
  
## Заметки  
 Эти значения передаются в качестве аргумента [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) метод, чтобы показать, какие поля  [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) структура быть инициализированным.  
  
 Эти значения используются также in `dwFields` элемент  `THREADPROPERTIES` структура для указания того, какие поля используются и допустимы.  
  
 Эти флаги могут объединяться с побитовый оператор `OR`.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)