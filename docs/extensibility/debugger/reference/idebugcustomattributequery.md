---
title: "IDebugCustomAttributeQuery | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugCustomAttributeQuery"
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugCustomAttributeQuery
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Представляет запрос для настраиваемых атрибутов для метода или типа.  
  
## Синтаксис  
  
```  
IDebugCustomAttributeQuery : IUnknown  
```  
  
## Методы  
 Этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|Извлекает настраиваемый атрибут заданного его имя.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|Задает в указанном настраиваемом атрибуте.|  
  
## Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll