---
title: "IScriptNode::GetCookie | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetCookie
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetCookie"
ms.assetid: 007339c6-a73a-4147-b3c0-cc041e467ecd
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IScriptNode::GetCookie
Возвращает приложение\- указанное значение, которое используется для связывания сценарий с объектом основного приложения.  
  
## Синтаксис  
  
```  
HRESULT GetCookie(  
   DWORD              *pdwCookie  
);  
```  
  
#### Параметры  
 `pdwCookie`  
 \[out\] для получения объекта `IScriptEntry`, приложение\- указанное значение файла cookie.  
  
 Для объекта `IScriptNode`, представляющий страницу, возвращает значение 0.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
  
## См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)