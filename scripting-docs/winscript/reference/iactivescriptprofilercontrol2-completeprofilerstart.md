---
title: "IActiveScriptProfilerControl2::CompleteProfilerStart | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2::CompleteProfilerStart"
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2::CompleteProfilerStart
Уведомляет профилировщик о том, что вы начали профилирование всех применимых обработчиков скриптов.  С помощью этого метода можно получить полный стек вызова, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется при запуске профилирования.  
  
## Синтаксис  
  
```  
HRESULT CompleteProfilerStart();  
```  
  
#### Параметры  
 Метод не принимает параметры.  
  
## Возвращаемое значение  
 Возвращает значение HRESULT.  Ниже приведены возможные значения:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Профилирование запустить нельзя.|  
|`S_FALSE`|Профилирование было запуститьо, если скрипт не выполнил.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Профилирование не включено.  Обратный вызов не был установлен.|  
|`E_OUTOFMEMORY`|Стек вызовов невозможно получить из\-за условия нехватки памяти.|  
  
## Заметки  
 Вызов `IActiveScriptProfilerControl2::CompleteProfilerStart` гарантирует, что отправитьы события для функций, уже находящихся в стеке вызова.  Этот метод следует вызывать после профилирующ начинается в любом обработчике скриптов, на вкладке текущий.  Метод может быть вызван для любого обработчика скриптов.  
  
## См. также  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [Интерфейс IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)