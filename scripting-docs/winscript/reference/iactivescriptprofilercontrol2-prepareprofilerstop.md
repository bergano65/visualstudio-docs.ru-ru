---
title: "IActiveScriptProfilerControl2::PrepareProfilerStop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2::PrepareProfilerStop"
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2::PrepareProfilerStop
Уведомляет профилировщик о том, что планируется остановить профилирование всех применимых обработчиков скриптов.  С помощью этого метода можно получить полный стек вызова, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется при остановке профилирования.  
  
## Синтаксис  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### Параметры  
 Метод не принимает параметры.  
  
## Возвращаемое значение  
 Возвращает значение HRESULT.  Ниже приведены возможные значения:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Профилирование не может быть запуститьо.|  
|`S_FALSE`|Профилирование было остановитьо, если скрипт не выполнил.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Профилирование не включено.|  
  
## Заметки  
 Вызов `IActiveScriptProfilerControl2::PrepareProfilerStop` гарантирует, что отправитьы события для функций в стеке вызова.  Этот метод должен быть вызван перед остановкой профилирования в обработчике скриптов, на вкладке текущий.  Метод может быть вызван для любого обработчика скриптов.  
  
## См. также  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [Интерфейс IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)