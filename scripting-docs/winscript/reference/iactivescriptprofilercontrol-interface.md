---
title: "Интерфейс IActiveScriptProfilerControl | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Интерфейс IActiveScriptProfilerControl
Реализуемый обработчиком сценариев является обозреватель, профилирования.  Обычно объект, средства `IActiveScriptProfilerControl` также реализуют интерфейс [IActiveScript](../../winscript/reference/iactivescript.md).  В этом случае можно получить дескриптор к интерфейсу `IActiveScriptProfilerControl` путем вызова метода `IUnknown::QueryInterface` на объект.  Интерфейс предоставляет необходимые методы для остановки и запуска профилирования в обработчике скриптов.  
  
## Методы  
  
|Метод|Описание|  
|-----------|--------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|При профилировании начинается на обработчике скриптов.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Задает маску события профилировщика в обработчике скриптов.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Стопы при профилировании на обработчик скриптов.|  
  
## См. также  
 [Интерфейсы профилировщика активных скриптов](../../winscript/reference/active-script-profiler-interfaces.md)