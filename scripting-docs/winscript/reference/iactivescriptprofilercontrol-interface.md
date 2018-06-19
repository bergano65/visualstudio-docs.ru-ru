---
title: Интерфейс IActiveScriptProfilerControl | Документы Microsoft
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
ms.openlocfilehash: f0d598302ae78ca0b2a1e7c1f94c949800378a2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724674"
---
# <a name="iactivescriptprofilercontrol-interface"></a>Интерфейс IActiveScriptProfilerControl
Реализован обработчик скриптов, которая поддерживает профилирования. Как правило, объект, реализующий интерфейс `IActiveScriptProfilerControl` также реализует [IActiveScript](../../winscript/reference/iactivescript.md) интерфейса. В этом случае можно получить дескриптор `IActiveScriptProfilerControl` интерфейса путем вызова `IUnknown::QueryInterface` метод для обработки объекта. Интерфейс предоставляет методы, необходимые для остановки и запуска профилирования на обработчик скриптов.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Начинает профилирование в обработчик сценариев.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Задает маску события профилировщика в обработчик сценариев.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Останавливает профилирование в обработчик сценариев.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы профилировщика активных скриптов](../../winscript/reference/active-script-profiler-interfaces.md)