---
title: "CONTEXT_INFO_FIELDS | Microsoft Docs"
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
  - "CONTEXT_INFO_FIELDS"
helpviewer_keywords: 
  - "Перечисление CONTEXT_INFO_FIELDS"
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# CONTEXT_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Указывает, какую информацию, которую необходимо извлечь сведения о контексте памяти.  
  
## Синтаксис  
  
```cpp#  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```c#  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## Члены  
 CIF\_MODULEURL  
 Инициализируйте и использование `bstrModuleUrl` поле   [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) структура.  
  
 CIF\_FUNCTION  
 Инициализируйте и использование `bstrFunction` поле   `CONTEXT_INFO` структура.  
  
 CIF\_FUNCTIONOFFSET  
 Инициализируйте и использование `posFunctionOffset` поле   `CONTEXT_INFO` структура.  
  
 CIF\_ADDRESS  
 Инициализируйте и использование `bstrAddress` поле   `CONTEXT_INFO` структура.  
  
 CIF\_ADDRESSOFFSET  
 Инициализируйте и использование `bstrAddressOffset` поле   `CONTEXT_INFO` структура.  
  
 CIF\_ALLFIELDS  
 Инициализируйте и использование все поля `CONTEXT_INFO` структура.  
  
## Заметки  
 Эти значения передаются параметром к [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) метод, чтобы показать, какие поля  [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) структура быть инициализированным.  
  
 Эти флаги также используются для указания того, какие поля `CONTEXT_INFO` используемая структура и допустимы, если структура возвращается.  
  
 Эти значения могут объединяться с побитовый оператор ИЛИ.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)