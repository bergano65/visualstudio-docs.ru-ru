---
title: "IScriptEntry::SetBody | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetBody
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetBody"
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IScriptEntry::SetBody
Устанавливает текст, в тело блока скрипта `IScriptEntry` или сценария `IScriptScriptlet`.  
  
## Синтаксис  
  
```  
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### Параметры  
 `psz`  
 \[in\] для блока скрипта `IScriptEntry`, заключенное в теги `psz` текст скрипта.  
  
 Для блока функции `IScriptEntry`, `psz` тело функции.  
  
 Для объекта `IScriptScriptlet` \(который является производным от `IScriptEntry`\), `psz` текст скрипта скрипта.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
  
## См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)