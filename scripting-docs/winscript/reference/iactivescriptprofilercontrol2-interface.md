---
title: "Интерфейс IActiveScriptProfilerControl2 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2 — интерфейс"
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Интерфейс IActiveScriptProfilerControl2
Предоставляет методы, добавляющие возможность запустить или остановить профилирование, если скрипт выполняется.  
  
## Методы  
  
|Метод|Описание|  
|-----------|--------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|Уведомляет профилировщик о том, что вы начали профилирование всех применимых обработчиков скриптов.  Это позволяет получить полный стек вызова, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется при запуске профилирования.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|Уведомляет профилировщик о том, что планируется остановить профилирование всех применимых обработчиков скриптов.  Это позволяет получить полный стек вызова, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется при остановке профилирования.|  
  
## См. также  
 [Интерфейс IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)   
 [Интерфейсы профилировщика активных скриптов](../../winscript/reference/active-script-profiler-interfaces.md)