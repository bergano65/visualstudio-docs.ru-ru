---
title: Интерфейс IActiveScriptProfilerCallback | Документация Майкрософт
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
ms.openlocfilehash: 2511b3e622dfa977c0ed05212203ad59fb0e71bd
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345868"
---
# <a name="iactivescriptprofilercallback-interface"></a>Интерфейс IActiveScriptProfilerCallback
Предоставляет методы, используемые обработчиком сценариев, чтобы уведомить объект профилировщика при возникновении событий. Этот интерфейс реализуется объектом профилировщика.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Вызывается для инициализации объект профилировщика при каждом запуске профилирования на обработчик скриптов.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Вызывается, чтобы освободить и освободить объект профилировщика, каждый раз, когда профилирование останавливается на обработчик скриптов.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Уведомляет профилировщик, что объект, который обработчик скриптов компиляции сценария.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Уведомляет профилировщик, что объект, который обработчик скриптов обнаружил функцию, при компиляции сценария.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Уведомляет объект профилировщика, который обработчик скриптов должен выполнить вызов функции, которая не является вызовом в объектной модели документа (DOM).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Уведомляет профилировщик, что объект, чтобы вызывать по завершении выполнения функции обработчика скриптов, не является вызов в модель DOM.|  
  
## <a name="remarks"></a>Примечания  
 Уведомление вызовов функций в объектной модели документа (DOM) предоставлено [интерфейс IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
>  Чтобы добавить возможность запуска и остановки профилирования, при выполнении сценарий, используйте следующие методы. С помощью этих методов, можно получить полный стек вызовов, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется при запуске или остановке профилирования.  
> 
> - Вызовите [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) для уведомления профилировщика, что вы запустили профилирования.  
>   -   Вызовите [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) для уведомления профилировщика, что будет скоро остановить профилирование.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы профилировщика активных скриптов](../../winscript/reference/active-script-profiler-interfaces.md)