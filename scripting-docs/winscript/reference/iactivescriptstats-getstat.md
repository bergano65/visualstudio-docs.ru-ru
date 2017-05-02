---
title: "IActiveScriptStats::GetStat | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStats.GetStat
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptStats::GetStat"
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats::GetStat
Один из стандартных получения статистики скрипта.  
  
## Синтаксис  
  
```  
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### Параметры  
 `stid`  
 \[in\] определяет, статистика.  Должно быть значение:  
  
|Константа|Значение|Описание|  
|---------------|--------------|--------------|  
|SCRIPTSTAT\_STATEMENT\_COUNT|1|Возвращает количество выполненных выписок поскольку были сброситьы started скрипт или статистики.|  
  
 `pluHi`  
 \[out\] старшие 32 64 разрядного целого числа без знака, представляющее счетчик.  
  
 `pluLo`  
 \[out\] младшие 32 64 разрядного целого числа без знака, представляющее счетчик.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются значениями в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод возвращает одно из стандартных статистики скрипта.  
  
## См. также  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [Интерфейс IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)