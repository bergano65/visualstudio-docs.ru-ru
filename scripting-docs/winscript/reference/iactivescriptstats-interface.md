---
title: "Интерфейс IActiveScriptStats | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptStats — интерфейс"
ms.assetid: dbe84d6f-1b77-4877-aced-cd4e01ead5b5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IActiveScriptStats
Позволяет узлу запроса статистика выполнения скрипта.  Основное приложение может использовать эти сведения для определения, является ли скрипт принимал слишком много времени.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IActiveScriptStats` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)|Один из стандартных получения статистики скрипта.|  
|[IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)|Возвращает пользовательское статистику скрипта.|  
|[IActiveScriptStats::ResetStats](../../winscript/reference/iactivescriptstats-resetstats.md)|Сбросить статистику для этого сценария.|