---
title: "IDebugActivateDocumentEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugActivateDocumentEvent2"
helpviewer_keywords: 
  - "Интерфейс IDebugActivateDocumentEvent2"
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugActivateDocumentEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Отладчик \(DE\) использует этот интерфейс для запроса документа.  
  
## Синтаксис  
  
```  
IDebugActivateDocumentEvent2 : IUnknown  
```  
  
## Примечания по реализации  
 DE реализующий этот интерфейс, когда необходимо исходный файл его открытия.  Этот интерфейс реализуется только обработчиков отладки, которые работают с переводчиков скрипта или его часть.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован в одном объекте, как этот интерфейс \(SDM использует  [QueryInterface](/visual-cpp/atl/queryinterface) доступ  `IDebugEvent2` интерфейс\).  
  
## Замечания для вызывающих объектов  
 DE создает и отправляет этот объект события, когда необходимо иметь исходный файл его открытия.  Событие отправляется с помощью IDebugEventCallback2 функция обратного вызова, предоставляемая SDM, когда он вложен в отлаживаемом программе.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugActivateDocumentEvent2`.  
  
|Методы|Описание|  
|------------|--------------|  
|[GetDocument](../Topic/IDebugActivateDocumentEvent2::GetDocument.md)|Возвращает документ активировать.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Возвращает контекст рисования, описывающий расположение в документе.|  
  
## Заметки  
 Типичный сценарий, в котором этот интерфейс используется, если происходит ошибка синтаксического анализа в коде скрипта на странице HTML скрипт DE отправляет этот интерфейс SDM, что документ с ошибкой синтаксического анализа можно отобразить.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)