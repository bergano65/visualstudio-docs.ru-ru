---
title: "NATIVE_ADDRESS | Microsoft Docs"
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
  - "NATIVE_ADDRESS"
helpviewer_keywords: 
  - "Структура NATIVE_ADDRESS"
ms.assetid: 7a0cd085-bfc8-45cc-a3d4-4459070e207a
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# NATIVE_ADDRESS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Эта структура представляет собственный адрес.  
  
## Синтаксис  
  
```cpp  
typedef struct _tagNATIVE_ADDRESS {  
   DWORD unknown;  
} NATIVE_ADDRESS;  
```  
  
```c#  
public struct NATIVE_ADDRESS {  
   public uint unknown;  
}  
```  
  
## Термины  
 unknown  
 Смысл этого собственный адрес \(зависит от того, среда выполнения и операционная система\).  
  
## Заметки  
 Эта структура является частью соединения в [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) когда структура  `dwKind` поле   `DEBUG_ADDRESS_UNION` структура имеет значение  `ADDRESS_KIND_NATIVE` \(значение  [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) перечисление\).  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)