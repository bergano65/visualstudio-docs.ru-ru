---
title: Интерфейс IActiveScriptProfilerControl | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef127e3a4463d112b9ea424702fb2650c80cce7d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571598"
---
# <a name="iactivescriptprofilercontrol-interface"></a>Интерфейс IActiveScriptProfilerControl
Реализуется обработчиком скриптов, поддерживающим профилирование. Как правило, объект, реализующий `IActiveScriptProfilerControl`, также реализует интерфейс [IActiveScript](../../winscript/reference/iactivescript.md) . В этом случае можно получить маркер интерфейса `IActiveScriptProfilerControl`, вызвав метод `IUnknown::QueryInterface` объекта. Интерфейс предоставляет необходимые методы для остановки и запуска профилирования в обработчике скриптов.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Запускает профилирование в обработчике скриптов.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Задает маску событий профилировщика в обработчике скриптов.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Останавливает профилирование в обработчике скриптов.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы профилировщика активных скриптов](../../winscript/reference/active-script-profiler-interfaces.md)