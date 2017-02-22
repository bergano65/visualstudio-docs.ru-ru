---
title: "IDebugProcessQueryProperties | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessQueryProperties"
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessQueryProperties
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс реализуется интерфейс расширения: IDebugProcess2 при реализации.  Он позволяет разработчик, чтобы получить сведения о среде процесса отладки.  
  
## Синтаксис  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## Примечания по реализации  
 Реализуйте этот интерфейс для получения сведений о среде выполнения процесса отладки.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugProcessQueryProperties`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[QueryProperty](../Topic/IDebugProcessQueryProperties::QueryProperty.md)|Запросы для значения свойства.|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Запросы для значений свойств.|  
  
## Заметки  
 Этот интерфейс реализуется редко.  
  
## Требования  
 Заголовок: Portpriv.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)