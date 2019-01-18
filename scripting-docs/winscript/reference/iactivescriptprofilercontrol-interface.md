---
title: Интерфейс IActiveScriptProfilerControl | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7caa09f384ce460a3e73b21b10d6d8022182dde7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349495"
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