---
title: Интерфейс IActiveScriptProfilerCallback2 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25f9616497192659df67feedfe16bd9ea0c5e3b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577304"
---
# <a name="iactivescriptprofilercallback2-interface"></a>Интерфейс IActiveScriptProfilerCallback2
Предоставляет методы, используемые обработчиком скриптов для уведомления объекта профилировщика при возникновении событий модель DOM (DOM). Этот интерфейс реализуется объектом Profiler.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Уведомляет объект профилировщика о том, что обработчик скриптов будет выполнять вызов функции DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Уведомляет объект профилировщика, что обработчик скриптов завершил выполнение вызова функции DOM.|  
  
## <a name="remarks"></a>Заметки  
 Интерфейс `IActiveScriptProfilerCallback2`, впервые выпущенный в Internet Explorer 9.  
  
 Уведомления о вызовах функций, которые не являются вызовами модели DOM, предоставляются [интерфейсом IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
> Чтобы добавить возможность запуска и отмены профилирования при выполнении скрипта, вызовите следующие методы. Используя эти методы, можно получить полный стек вызовов, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется при запуске или выключении профилирования.  
> 
> - Вызовите [IActiveScriptProfilerControl2:: комплетепрофилерстарт](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) , чтобы уведомить профилировщик о запуске профилирования.  
>   - Вызовите [IActiveScriptProfilerControl2::P репарепрофилерстоп](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) , чтобы уведомить профилировщик о том, что вскоре будет прекращено профилирование.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы профилировщика активных скриптов](../../winscript/reference/active-script-profiler-interfaces.md)