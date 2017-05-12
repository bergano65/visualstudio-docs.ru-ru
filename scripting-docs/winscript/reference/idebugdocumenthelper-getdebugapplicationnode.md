---
title: "IDebugDocumentHelper::GetDebugApplicationNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.GetDebugApplicationNode
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::GetDebugApplicationNode"
ms.assetid: ecd18803-beb4-4ac2-9702-cc9e8a12c395
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::GetDebugApplicationNode
Возвращает узел приложения отладки, соответствующий данному документу.  
  
## Синтаксис  
  
```  
HRESULT GetDebugApplicationNode(  
   IDebugApplicationNode**  ppdan  
);  
```  
  
#### Параметры  
 `ppdan`  
 \[out\] узел приложения отладки, соответствующий данному документу.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Возвращает узел приложения отладки, соответствующий данному документу.  
  
## См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)