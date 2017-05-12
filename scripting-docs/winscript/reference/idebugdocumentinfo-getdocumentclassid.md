---
title: "IDebugDocumentInfo::GetDocumentClassId | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentInfo.GetDocumentClassId
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentInfo::GetDocumentClassId"
ms.assetid: 3b858794-2c0c-42ba-b98c-cd820ebace20
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentInfo::GetDocumentClassId
Возвращает `CLSID`, указывающие тип документа.  
  
## Синтаксис  
  
```  
HRESULT GetDocumentClassId(  
   CLSID*  pclsidDocument  
);  
```  
  
#### Параметры  
 `pclsidDocument`  
 \[out\] значение `CLSID`, указывающие тип документа.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод позволяет интегрированной среды разработки основного приложения телезрителям отладчика к пользовательским для этого документа.  
  
 Если документ не имеет отображаются данные, то возвращаемое значение `pclsidDocument``CLSID_NULL`.  
  
## См. также  
 [Интерфейс IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)