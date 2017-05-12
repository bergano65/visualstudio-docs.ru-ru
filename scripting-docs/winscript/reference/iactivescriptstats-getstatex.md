---
title: "IActiveScriptStats::GetStatEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStats.GetStatEx
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptStats::GetStatEx"
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats::GetStatEx
Возвращает пользовательское статистику скрипта.  
  
## Синтаксис  
  
```  
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### Параметры  
 `guid`  
 \[in\] определяет, статистика.  Семантика что статистика соответствует конкретному GUID полностью определенный обработчик.  
  
 `pluHi`  
 \[out\] старшие 32 64 разрядного целого числа без знака, представляющее счетчик.  
  
 `pluLo`  
 \[out\] младшие 32 64 разрядного целого числа без знака, представляющее счетчик.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Метод не реализован.|  
  
## Заметки  
 Этот метод позволяет пользовательский обработчик скриптов для возвращения статистики понятным к настраиваемому узлу.  
  
> [!NOTE]
>  В настоящее время этот метод не реализован.  
  
## См. также  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [Интерфейс IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)