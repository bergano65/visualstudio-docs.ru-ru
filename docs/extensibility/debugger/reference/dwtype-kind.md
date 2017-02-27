---
title: "dwTYPE_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "dwTYPE_KIND"
helpviewer_keywords: 
  - "Перечисление dwTYPE_KIND"
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# dwTYPE_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет способ интерпретации тип IDebugField объект.  
  
## Синтаксис  
  
```cpp#  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```c#  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### Параметры  
 TYPE\_KIND\_METADATA  
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) объединение должно интерпретироваться как a  [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md) структура.  
  
 TYPE\_KIND\_PDB  
 `TYPE_INFO` объединение должно интерпретироваться как a  [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md) структура.  
  
 TYPE\_KIND\_BUILT  
 `TYPE_INFO` объединение должно интерпретироваться как a  [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md) структура.  
  
## Заметки  
 Значения этого перечисления отображаются в `dwKind` поле   [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) структура и используется для определения, как интерпретировать  `type` член объединения.  `TYPE_INFO` структура возвращается вызовом  [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) метод.  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)