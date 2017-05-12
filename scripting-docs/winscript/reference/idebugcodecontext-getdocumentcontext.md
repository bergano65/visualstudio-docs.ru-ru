---
title: "IDebugCodeContext::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugCodeContext.GetDocumentContext
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugCodeContext::GetDocumentContext"
ms.assetid: 9fe17b65-3a8c-4d21-9b66-0e4ff303af72
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCodeContext::GetDocumentContext
Возвращает контекст рисования, связанный с данным контекстом кода.  
  
## Синтаксис  
  
```  
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### Параметры  
 `ppsc`  
 \[out\] контекст рисования, связанный с данным контекстом кода.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Для текстовых документов, диапазон позиции символа должно включать текст для всей выписки.  Это позволяет интегрированная среда разработки отладчика, чтобы выбрать текущую выписка источника.  
  
## См. также  
 [Интерфейс IDebugCodeContext](../../winscript/reference/idebugcodecontext-interface.md)