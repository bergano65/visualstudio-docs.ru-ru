---
title: "IScriptScriptlet::SetEventName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.SetEventName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::SetEventName"
ms.assetid: 8787d58b-7deb-415b-b0e9-d2f0eb72dcf7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IScriptScriptlet::SetEventName
Задает имя события, которое сопоставитьо со скриптом.  
  
## Синтаксис  
  
```  
HRESULT SetEventName(  
   LPCOLESTR          psz  
);  
```  
  
#### Параметры  
 `psz`  
 \[in\] буфер, содержащий имя события, которое сопоставитьо с объектом `IScriptScriptlet`.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
  
## См. также  
 [Интерфейс IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)