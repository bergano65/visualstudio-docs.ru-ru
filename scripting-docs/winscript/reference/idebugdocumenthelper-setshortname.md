---
title: "IDebugDocumentHelper::SetShortName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetShortName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetShortName"
ms.assetid: 811a444b-0ea4-4374-9d4c-4f7713bdd1ff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetShortName
Задает короткое имя документа.  
  
## Синтаксис  
  
```  
HRESULT SetShortName(  
   LPCOLESTR  pszShortName  
);  
```  
  
#### Параметры  
 `pszShortName`  
 \[in\] значение null\- завершенных строка, содержащая короткое имя документа.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод устанавливает новое короткое имя документа.  
  
## См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)