---
title: 'IActiveScriptProfilerControl2:: Комплетепрофилерстарт | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0230ecb480792b5b24b7375f5b95926735d0a61
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571557"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Уведомляет профилировщик о запуске профилирования для всех применимых обработчиков скриптов. С помощью этого метода можно получить полный стек вызовов, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется при запуске профилирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Параметры  
 Метод не принимает никаких параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение HRESULT. Ниже приведены возможные значения.  
  
|Возвращаемое значение|Смысл|  
|------------------|-------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Не удается запустить профилирование.|  
|`S_FALSE`|Профилирование было запущено, когда сценарий не выполнялся.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Профилирование не включено. Обратный вызов не задан.|  
|`E_OUTOFMEMORY`|Не удается получить стек вызовов из-за нехватки памяти.|  
  
## <a name="remarks"></a>Заметки  
 Вызов `IActiveScriptProfilerControl2::CompleteProfilerStart` гарантирует отправку событий для функций, уже находящиеся в стеке вызовов. Этот метод должен вызываться после запуска профилирования на любом обработчике скриптов, который находится на текущей вкладке. Метод может быть вызван для любого обработчика скриптов.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptProfilerControl2::P репарепрофилерстоп](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)    
 [Интерфейс IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)