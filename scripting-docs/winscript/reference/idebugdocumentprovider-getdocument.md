---
title: "IDebugDocumentProvider::GetDocument | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentProvider.GetDocument
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentProvider::GetDocument"
ms.assetid: da67dab0-778a-4dab-8ca3-055ee7a4f141
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentProvider::GetDocument
Приводит к тому, что документ быть создан, если он еще не существует.  
  
## Синтаксис  
  
```  
HRESULT GetDocument(  
   IDebugDocument**  ppssd  
);  
```  
  
#### Параметры  
 `ppssd`  
 \[out\] документ отладки, соответствующий документу.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод приводит к тому, что документ быть создан, если он еще не существует.  
  
## См. также  
 [Интерфейс IDebugDocumentProvider](../../winscript/reference/idebugdocumentprovider-interface.md)