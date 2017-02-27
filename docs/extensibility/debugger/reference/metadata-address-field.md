---
title: "METADATA_ADDRESS_FIELD | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_FIELD"
helpviewer_keywords: 
  - "Структура METADATA_ADDRESS_FIELD"
ms.assetid: 15ab45fe-6b3b-4e09-880b-31b34f523607
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# METADATA_ADDRESS_FIELD
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Эта структура представляет адрес поля класса или структуры.  
  
## Синтаксис  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_FIELD {  
   _mdToken tokField;  
} METADATA_ADDRESS_FIELD  
```  
  
```c#  
public struct METADATA_ADDRESS_FIELD {  
   public int tokField;  
}  
```  
  
## Термины  
 tokField  
 Идентификатор токена поля.  
  
 \[C\+\+\] `_mdToken` a  `typedef` для обновления 32 \(sp2\)  `int`.  
  
## Заметки  
 Эта структура является частью соединения в [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) когда структура  `dwKind` поле   `DEBUG_ADDRESS_UNION` структура имеет значение  `ADDRESS_KIND_FIELD` \(значение  [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) перечисление\).  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)