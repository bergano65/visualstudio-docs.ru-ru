---
title: "IActiveScriptSiteInterruptPoll::QueryContinue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteInterruptPoll.QueryContinue
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteInterruptPoll::QueryContinue"
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteInterruptPoll::QueryContinue
Позволяет основному приложению определить, что скрипт должен быть завершен.  
  
## Синтаксис  
  
```  
HRESULT QueryContinue();  
```  
  
#### Параметры  
 Этот метод не принимает параметры.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Вызов завершился успешно и основное приложение разрешает продолжить выполнение скриптов.|  
|`S_FALSE`|Вызов завершился успешно и основное приложение запрашивает, что скрипт.|  
  
## Заметки  
 Скрипт размещенного должен завершить если возвращаемое значение метода `QueryContinue` не будет `S_ОК`.  Возвращаемое значение `S_FALSE` указывает, что запросы основного приложения явно, скрипт.  
  
 Многопоточные узел может использовать метод `IActiveScript::InterruptScriptThread` для выполнения скриптов.  
  
## См. также  
 [Интерфейс IActiveScriptSiteInterruptPoll](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)