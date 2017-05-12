---
title: "IScriptScriptlet::SetSubItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.SetSubItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::SetSubItemName"
ms.assetid: 619f222f-b4c3-4c7b-9d19-e4e7037343a6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IScriptScriptlet::SetSubItemName
Задает последний идентификатор в полном имени узла объекта скрипта.  
  
## Синтаксис  
  
```  
HRESULT SetSubItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### Параметры  
 `psz`  
 Если имя скрипта узла, полное имеет более одного уровня, то `psz` адрес буфера идентификатора на втором уровне.  
  
 Если имя скрипта узла, полное имеет один уровень, `psz` адрес буфера идентификатора на первом уровне.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
  
## См. также  
 [Интерфейс IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)