---
title: "IDebugGenericParamField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugGenericParamField"
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugGenericParamField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Представляет параметр универсального типа управляемого кода.  
  
## Синтаксис  
  
```  
IDebugGenericParamField : IDebugField  
```  
  
## Примечания по реализации  
 Используется для поддержки универсальных шаблонов.  
  
## Методы  
 в дополнение к методам на IDebugField интерфейс этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Возвращает количество ограничений, связанных с данным родовым параметром.|  
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Извлекает ограничения, связанные с этим родовым параметром.|  
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Возвращает флаги для данного универсального параметра.|  
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Извлекает индекс данного универсального параметра.|  
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Извлекает имя данного универсального параметра.|  
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Извлекает владельца типа или метода данного универсального параметра.|  
  
## Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll