---
title: "Интерфейс IActiveScriptProfilerCallback2 | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dc9fcd8ca4afec0fb474c0f3a7317b608c7c9f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback2-interface"></a>Интерфейс IActiveScriptProfilerCallback2
Предоставляет методы, используемые обработчиком сценариев, чтобы уведомить объект профилировщика при возникновении событий объектной модели документа (DOM). Этот интерфейс реализуется объектом профилировщика.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Уведомляет объект профилировщика, которую планируется выполнить вызов функции DOM обработчика скриптов.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Уведомляет профилировщик, что объект, который модуль создания скриптов завершения выполнения вызова функции DOM.|  
  
## <a name="remarks"></a>Примечания  
 `IActiveScriptProfilerCallback2` Интерфейс первого выпуска с Internet Explorer 9.  
  
 Уведомление вызовов функций, не являющихся вызовами в DOM предоставлено [интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
>  Чтобы добавить возможность запуска и остановки профилирования при выполнении сценария, используйте следующие методы. С помощью этих методов, можно получить полный стек вызовов, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется при запуске или остановке профилирования.  
>   
>  -   Вызовите [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) для уведомления профилировщика о том, что вы запустили профилирования.  
> -   Вызовите [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) для уведомления профилировщика о том, что будет скоро остановить профилирование.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы профилировщика активных скриптов](../../winscript/reference/active-script-profiler-interfaces.md)