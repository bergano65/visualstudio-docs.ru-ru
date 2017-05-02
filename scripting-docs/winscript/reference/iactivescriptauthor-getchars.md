---
title: "IActiveScriptAuthor::GetChars | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetChars
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetChars"
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IActiveScriptAuthor::GetChars
Возвращает набор символов завершения для контекста выполнения.  
  
## Синтаксис  
  
```  
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### Параметры  
 `fRequestedList`  
 \[in\] контекст выполнения.  
  
|Константа|Значение|Описание|  
|---------------|--------------|--------------|  
|SCRIPT\_CMPL\_ENUM\_TRIGGER|0x0001|Запрашивающий перечисление слева.|  
|SCRIPT\_CMPL\_MEMBER\_TRIGGER|0x0002|Запрашивает контекст выполнения элемента.|  
|SCRIPT\_CMPL\_PARAM\_TRIGGER|0x0003|Запрашивает список параметров.|  
|SCRIPT\_CMPL\_COMMIT|0x0004|Запрашивает завершение списка параметров.|  
  
 `pbstrChars`  
 \[out\] символы, соответствующие контексту выполнения.  
  
|Параметр `fRequestedList`|Возвращаемые символы|  
|-------------------------------|--------------------------|  
|SCRIPT\_CMPL\_ENUM\_TRIGGER|"."|  
|SCRIPT\_CMPL\_MEMBER\_TRIGGER|"\="|  
|SCRIPT\_CMPL\_PARAM\_TRIGGER|"\("|  
|SCRIPT\_CMPL\_COMMIT|"\(\)"|  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
  
## См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)