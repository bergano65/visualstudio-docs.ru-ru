---
title: "IScriptEntry::SetText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ISetEntry::SetText"
ms.assetid: 4605481b-7707-43d1-ab78-a9207d0cf6fe
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::SetText
Устанавливает текст, соответствующий блок скрипта `IScriptEntry` или исходный код, содержащийся в обработчике событий `IScriptScriptlet`.  
  
## Синтаксис  
  
```  
HRESULT SetText(  
   LPCOLESTR          psz  
);  
```  
  
#### Параметры  
 `psz`  
 \[in\] текст блока скрипта `IScriptEntry` или исходный код обработчика событий `IScriptScriptlet`.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
  
## См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)