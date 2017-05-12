---
title: "IDebugDocumentHelper::BringDocumentToTop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.BringDocumentToTop
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::BringDocumentToTop"
ms.assetid: 91bdbb05-6f79-4b07-a707-838cb75a770f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::BringDocumentToTop
Помещает данный документ в верхней части пользовательского интерфейса отладчика.  
  
## Синтаксис  
  
```  
HRESULT BringDocumentToTop();  
```  
  
#### Параметры  
 Этот метод не принимает параметры.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод запускает отладчик, если он еще не запущен.  
  
## См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)