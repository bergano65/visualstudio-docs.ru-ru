---
title: Интерфейс IActiveScriptProfilerCallback | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ae520dcb36e00dfaba8702db6294a5a47484b0a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571714"
---
# <a name="iactivescriptprofilercallback-interface"></a>Интерфейс IActiveScriptProfilerCallback
Предоставляет методы, используемые обработчиком скриптов для уведомления объекта профилировщика о возникновении событий. Этот интерфейс реализуется объектом Profiler.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Вызывается для инициализации объекта профилировщика при запуске профилирования в обработчике скриптов.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Вызывается для освобождения и освобождения объекта профилировщика при остановке профилирования в обработчике скриптов.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Уведомляет объект профилировщика о том, что обработчик скриптов выполнил компиляцию скрипта.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Уведомляет объект профилировщика о том, что обработчик скриптов обнаружил функцию при компиляции скрипта.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Уведомляет объект профилировщика о том, что обработчик скриптов собирается выполнить вызов функции, который не является вызовом модель DOM (DOM).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Уведомляет объект профилировщика о том, что обработчик скриптов завершил выполнение вызова функции, который не является вызовом модели DOM.|  
  
## <a name="remarks"></a>Заметки  
 Уведомление о вызовах функций в модель DOM (DOM) предоставляется [интерфейсом IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
> Чтобы добавить возможность запуска и отмены профилирования при выполнении скрипта, вызовите следующие методы. Используя эти методы, можно получить полный стек вызовов, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется при запуске или выключении профилирования.  
> 
> - Вызовите [IActiveScriptProfilerControl2:: комплетепрофилерстарт](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) , чтобы уведомить профилировщик о запуске профилирования.  
>   - Вызовите [IActiveScriptProfilerControl2::P репарепрофилерстоп](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) , чтобы уведомить профилировщик о том, что вскоре будет прекращено профилирование.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы профилировщика активных скриптов](../../winscript/reference/active-script-profiler-interfaces.md)