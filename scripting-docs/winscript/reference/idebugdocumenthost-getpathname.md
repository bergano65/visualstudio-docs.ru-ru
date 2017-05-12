---
title: "IDebugDocumentHost::GetPathName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetPathName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetPathName"
ms.assetid: 8abe2a86-e467-4ac9-8ccb-8761141bfa0d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetPathName
Возвращает полный путь и имя файла исходного файла документа.  
  
## Синтаксис  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### Параметры  
 `pbstrLongName`  
 \[out\] строка, содержащая а длинное имя.  
  
 `pfIsOriginalFile`  
 \[out\] пометить a, значение true, если `pbstrLongName` относится к исходному файлу документа; в противном случае – значение false.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Ни один исходный файл можно создать или задать.|  
  
## Заметки  
 Этот метод возвращает полный путь и имя файла исходного файла документа.  
  
## См. также  
 [Интерфейс IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)