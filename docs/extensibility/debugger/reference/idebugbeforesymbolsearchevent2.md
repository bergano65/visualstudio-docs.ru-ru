---
title: "IDebugBeforeSymbolSearchEvent2 | Microsoft Docs"
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
  - "Интерфейс IDebugBeforeSymbolSearchEvent2"
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBeforeSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Отладчик \(DE\) отправляет этот интерфейс для сеанса отладки \(SDM\) диспетчер для задания сообщение строки состояния во время загрузки символов.  
  
## Синтаксис  
  
```  
IDebugBeforeSymbolSearchEvent2 : IUnknown  
```  
  
## Примечания по реализации  
 DE реализующий этот интерфейс, когда он должен задать сообщение строки состояния во время загрузки символов.  Этот интерфейс реализуется только обработчиков отладки, которые работают с переводчиков скрипта или его часть.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован в одном объекте, как этот интерфейс \(SDM использует  **QueryInterface** доступ  **IDebugEvent2** интерфейс\).  
  
## Замечания для вызывающих объектов  
 DE создает и отправляет этот объект события, когда он должен поместить сообщение строки состояния во время загрузки символов.  Событие отправляется с помощью IDebugEventCallback2 функция обратного вызова, предоставляемая SDM, когда он вложен в отлаживаемом программе.  
  
## Методы  
 В следующей таблице показаны методы `IDebugBeforeSymbolSearchEvent2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Извлекает имя в настоящее время, отлаживанными модуля.|  
  
## Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll