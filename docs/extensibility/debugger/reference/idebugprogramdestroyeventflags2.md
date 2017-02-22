---
title: "IDebugProgramDestroyEventFlags2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugProgramDestroyEventFlags2"
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Разрешает ядро отладки для переопределения по умолчанию применяются расширения функциональности [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Пользовательский интерфейс после завершения сеанса отладки.  
  
## Синтаксис  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## Примечания по реализации  
 Этот интерфейс реализуется определяемая обработчиков отладки.  Полезно для узлов, которые может создать и удалить несколько программ со временем существования процесса.  
  
## Методы  
 В следующей таблице показаны методы `IDebugProgramDestroyEventFlags2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Извлекает программа destroy флаги.|  
  
## Заметки  
 По умолчанию применяются расширения функциональности [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Пользовательский интерфейс вернуться в режим конструктора, после того как все программы, отправленные программа разрушают событие.  Этот интерфейс позволяет обработчику отладки для изменения этой функциональности.  
  
## Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll