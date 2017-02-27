---
title: "IDebugDocumentPositionOffset2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugDocumentPositionOffset2"
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Представляет позицию в файле источника как сдвиг знака.  
  
## Синтаксис  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## Примечания по реализации  
 Реализованный средой разработки и отладки обработчики общим by.  
  
## Методы  
 В следующей таблице показаны методы `IDebugDocumentPositionOffset2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetRange](../Topic/IDebugDocumentPositionOffset2::GetRange.md)|Получает диапазон для позиции текущего документа.|  
  
## Заметки  
 Это возвращает такие же сведения, как и [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) но в пределах  `char` смещение от начала документа.  Это представляет документ как оно существовало бы на диске, т е одномерном массиве знаков, вместо линии и данных столбца, обычно возвращается.  
  
## Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)