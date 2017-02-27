---
title: "IDebugPortSupplierDescription2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugPortSupplierDescription2"
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortSupplierDescription2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Включает [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Пользовательский интерфейс для отображения текста внутри  **Сведения о транспорте** раздел   **Присоединение к процессу** диалоговое окно.  
  
## Синтаксис  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## Примечания по реализации  
 Этот интерфейс реализуется поставщиками порта.  
  
## Методы  
 В следующей таблице показаны методы `IDebugPortSupplierDescription2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Извлекает описание и метаданные описание поставщика порта.|  
  
## Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll