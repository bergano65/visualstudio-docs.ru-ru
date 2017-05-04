---
title: "Интерфейс IActiveScriptProfilerCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2 — интерфейс"
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Интерфейс IActiveScriptProfilerCallback2
Предоставляет методы, используемые обработчиком скриптов для уведомления профилировщика, когда объект события DOM.  Этот интерфейс реализуется объектом профилировщика.  
  
## Методы  
  
|Метод|Описание|  
|-----------|--------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Уведомляет профилировщик о том, что объект обработчика сценариев становится выполнить вызов функции DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Уведомляет объект профилировщика, завершенного обработчик скриптов выполняется вызов функции DOM.|  
  
## Заметки  
 Сначала освобожданный интерфейс `IActiveScriptProfilerCallback2` с Internet Explorer 9.  
  
 Уведомление вызовов функции, не входящие в модель DOM, предоставленный [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
>  Чтобы добавить возможность запустить и остановить профилирование, если скрипт выполняется, вызовите следующие методы.  С помощью этих методов можно получить полный стек вызова, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется при запуске или остановить профилирование.  
>   
>  -   Вызовите [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) для уведомления профилировщика, что вы начали профилирование.  
> -   Вызовите [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) для уведомления профилировщика, что вскоре остановите профилирования.  
  
## См. также  
 [Интерфейсы профилировщика активных скриптов](../../winscript/reference/active-script-profiler-interfaces.md)