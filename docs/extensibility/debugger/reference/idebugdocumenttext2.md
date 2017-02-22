---
title: "IDebugDocumentText2 | Microsoft Docs"
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
  - "IDebugDocumentText2"
helpviewer_keywords: 
  - "Интерфейс IDebugDocumentText2"
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentText2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет текстовый документ.  
  
## Синтаксис  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс, когда исходный код для этого необходимо предоставить в текстовой форме.  Поскольку это наиболее типичная случае, если DE реализует [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) интерфейс, он также должен реализовывать  `IDebugDocumentText2` интерфейс.  
  
## Замечания для вызывающих объектов  
 Используйте `QueryInterface` метод, чтобы получить этот интерфейс с  `IDebugDocument2` интерфейс.  
  
## Методы в том порядке Vtable  
 в дополнение к методам на `IDebugDocument2` интерфейс этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Получает размер текста в данной позиции в документе.|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Извлекает текст, расположенный на указанной позиции в документе.|  
  
## Заметки  
 Объект, реализующий этот интерфейс, должен также реализовывать <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> интерфейс, который предоставляет  <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> интерфейс  [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) объект.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)