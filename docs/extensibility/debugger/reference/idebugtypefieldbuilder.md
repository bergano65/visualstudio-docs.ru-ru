---
title: "IDebugTypeFieldBuilder | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugTypeFieldBuilder"
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugTypeFieldBuilder
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Представляет возможность создать поле, представляющее тип.  
  
## Синтаксис  
  
```  
IDebugTypeFieldBuilder : IUnknown  
```  
  
## Замечания для вызывающих объектов  
 Этот интерфейс полученного от поставщика символов.  
  
## Методы  
 Этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Создает объект, представляющий тип\-примитив.|  
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Создает указатель к заданному типу.|  
  
## Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll