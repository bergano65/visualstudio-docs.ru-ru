---
title: "Интерфейс IActiveScriptProfilerCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Интерфейс IActiveScriptProfilerCallback
Предоставляет методы, используемые обработчиком скриптов для уведомления профилировщика, когда объект события происходят.  Этот интерфейс реализуется объектом профилировщика.  
  
## Методы  
  
|Метод|Описание|  
|-----------|--------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Вызываемый для инициализации объект профилировщика при профилирующ начавшийся в обработчике скриптов.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Вызывается для освобождения и освободить объект профилировщика при остановке профилирования в обработчике скриптов.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Уведомляет профилировщик о том, что объект обработчика сценариев компилировал скрипт.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Уведомляет профилировщик о том, что объект обработчика сценариев обнаружил функция при компилировании скрипт.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Уведомляет профилировщик о том, что объект обработчика сценариев собирается выполнить вызов функции, не вызова в объектной модели документов \(DOM\).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Уведомляет объект профилировщика этот обработчик скриптов завершено выполнение вызова функции, не вызова в модели DOM.|  
  
## Заметки  
 Уведомление вызовов функций в объектной модели документов \(DOM\) предоставляется [Интерфейс IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
>  Чтобы добавить возможность запустить и остановить профилирование, если скрипт выполняется, вызовите следующие методы.  С помощью этих методов можно получить полный стек вызова, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется при запуске или остановить профилирование.  
>   
>  -   Вызовите [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) для уведомления профилировщика, что вы начали профилирование.  
> -   Вызовите [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) для уведомления профилировщика, что вскоре остановите профилирования.  
  
## См. также  
 [Интерфейсы профилировщика активных скриптов](../../winscript/reference/active-script-profiler-interfaces.md)