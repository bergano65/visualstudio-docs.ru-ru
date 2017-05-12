---
title: "IDebugDocumentTextAuthor::ReplaceText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextAuthor.ReplaceText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextAuthor::ReplaceText"
ms.assetid: f89304e6-5be0-45a5-947d-2c59c3c0a05e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextAuthor::ReplaceText
Замена текста в документе.  
  
## Синтаксис  
  
```  
HRESULT ReplaceText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToReplace,  
   OLECHAR  pcharText[]  
);  
```  
  
#### Параметры  
 `cCharacterPosition`  
 \[in\] начальное положение диапазона символов, которые необходимо заменить.  
  
 `cNumToReplace`  
 \[in\] количество символов, которые необходимо заменить.  
  
 `pcharText[]`  
 \[in\] буфер, содержащий новые символы для замены старых символы.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод заменяет текста в документе.  
  
## См. также  
 [Интерфейс IDebugDocumentTextAuthor](../../winscript/reference/idebugdocumenttextauthor-interface.md)