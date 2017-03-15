---
title: "IDebugExtendedField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugExtendedField"
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugExtendedField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Расширяет типы полей, которые доступны для поддержки универсальных шаблонов управляемого кода.  
  
## Синтаксис  
  
```  
IDebugExtendedField : IDebugField  
```  
  
## Методы  
 в дополнение к методам на IDebugField интерфейс этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Извлекает указанный расширенный тип поля.|  
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Определяет, если поле представляет тип закрыть.|  
  
## Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll