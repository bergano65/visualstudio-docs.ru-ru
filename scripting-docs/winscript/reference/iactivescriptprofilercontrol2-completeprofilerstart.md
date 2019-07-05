---
title: IActiveScriptProfilerControl2::CompleteProfilerStart | Документация Майкрософт
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
ms.openlocfilehash: 36a1f5d6a1401e2860b65a29c8e383627e83c6be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993028"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Уведомляет профилировщик о том, что вы запустили профилирования на всех применимых обработчиков сценариев. С помощью этого метода, можно получить полный стек вызовов, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется при запуске профилирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Параметры  
 Метод не принимает никаких параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение HRESULT. Ниже приведены возможные значения.  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Не удалось запустить профилирование.|  
|`S_FALSE`|Профилирование был запущен, когда не был запущен сценарий.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Профилирование не включено. Обратный вызов не задано.|  
|`E_OUTOFMEMORY`|Не удается получить стек вызовов из-за условием памяти.|  
  
## <a name="remarks"></a>Примечания  
 Вызов `IActiveScriptProfilerControl2::CompleteProfilerStart` гарантирует отправку событий для функции уже в стеке вызовов. Этот метод должен вызываться после профилирования запускается на любой обработчик скриптов, который находится на текущей вкладке. Метод может вызываться для любого обработчика скриптов.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [Интерфейс IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)