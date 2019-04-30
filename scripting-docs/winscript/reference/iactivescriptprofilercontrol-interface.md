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
ms.openlocfilehash: 86f4fb8dea97930f717800a14a27740b76eb6c2e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993063"
---
# <a name="iactivescriptprofilercontrol-interface"></a>Интерфейс IActiveScriptProfilerControl
Реализован обработчик скриптов, который поддерживает профилирование. Как правило, объект, реализующий `IActiveScriptProfilerControl` также реализует [IActiveScript](../../winscript/reference/iactivescript.md) интерфейс. В этом случае можно получить дескриптор `IActiveScriptProfilerControl` интерфейс путем вызова `IUnknown::QueryInterface` метода объекта. Интерфейс предоставляет необходимые методы для остановки и запуска профилирования на обработчик скриптов.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Запускает профилирование на обработчик скриптов.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Задает маску события профилировщика в обработчик сценариев.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Останавливает профилирование на обработчик скриптов.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы профилировщика активных скриптов](../../winscript/reference/active-script-profiler-interfaces.md)