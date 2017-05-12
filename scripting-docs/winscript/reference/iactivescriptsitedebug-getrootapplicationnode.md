---
title: "IActiveScriptSiteDebug::GetRootApplicationNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetRootApplicationNode
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetRootApplicationNode"
ms.assetid: 2393f566-6b97-47c0-8041-4dd7e3b1d3a3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetRootApplicationNode
Получает узел приложения, под которым должны быть добавитьы документы скрипта.  
  
## Синтаксис  
  
```  
HRESULT GetRootApplicationNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### Параметры  
 `ppdanRoot`  
 \[out\] узел приложения отладки, содержащий документы скрипта.  Может принимать значение `NULL`.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод возвращает узел приложения, под которым должны быть добавитьы документы скрипта.  Метод может возвращать `NULL` для `ppdanRoot` если документы скрипта должны верхнего уровня.  
  
## См. также  
 [Интерфейс IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)