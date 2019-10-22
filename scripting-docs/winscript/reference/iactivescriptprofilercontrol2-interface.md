---
title: Интерфейс IActiveScriptProfilerControl2 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2 interface
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7059868ae65c5093b24f342bd303ec70172171c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571528"
---
# <a name="iactivescriptprofilercontrol2-interface"></a>Интерфейс IActiveScriptProfilerControl2
Предоставляет методы, добавляющие возможность запуска или отмены профилирования при выполнении скрипта.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|Уведомляет профилировщик о запуске профилирования для всех применимых обработчиков скриптов. Это позволяет получить полный стек вызовов, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется при запуске профилирования.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|Уведомляет профилировщик о том, что вы собираетесь отключить профилирование для всех применимых обработчиков скриптов. Это позволяет получить полный стек вызовов, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется, когда вы останавливаете профилирование.|  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)  
 [Интерфейсы профилировщика активных скриптов](../../winscript/reference/active-script-profiler-interfaces.md)