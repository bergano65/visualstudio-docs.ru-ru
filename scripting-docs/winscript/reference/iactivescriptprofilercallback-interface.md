---
title: Интерфейс IActiveScriptProfilerCallback | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4dc4b9d4e3b1f83a37e64e3a85387fd378d3ca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724584"
---
# <a name="iactivescriptprofilercallback-interface"></a>Интерфейс IActiveScriptProfilerCallback
Предоставляет методы, используемые обработчиком сценариев, чтобы уведомить объект профилировщика при возникновении событий. Этот интерфейс реализуется объектом профилировщика.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Вызывается для инициализации объекта профилировщика при каждом запуске профилирования на обработчик скриптов.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Вызывается, чтобы освободить и освободить объект профилировщика при остановке профилирования на обработчик скриптов.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Уведомляет профилировщик, объект, который модуль создания скриптов компиляции сценария.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Уведомляет профилировщик, что объект, который модуль создания скриптов обнаружил функцию при компиляции сценария.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Уведомляет профилировщик объект, который обработчик скриптов выполнять вызов функции, который не является вызовом в объектной модели документа (DOM).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Уведомляет профилировщик, что объект, вызывать по завершении выполнения функцию обработчика скриптов, не вызывает в модель DOM.|  
  
## <a name="remarks"></a>Примечания  
 Уведомление вызовов функций в объектной модели документа (DOM) предоставлено [интерфейс IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
>  Чтобы добавить возможность запуска и остановки профилирования при выполнении сценария, используйте следующие методы. С помощью этих методов, можно получить полный стек вызовов, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется при запуске или остановке профилирования.  
>   
>  -   Вызовите [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) для уведомления профилировщика о том, что вы запустили профилирования.  
> -   Вызовите [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) для уведомления профилировщика о том, что будет скоро остановить профилирование.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы профилировщика активных скриптов](../../winscript/reference/active-script-profiler-interfaces.md)