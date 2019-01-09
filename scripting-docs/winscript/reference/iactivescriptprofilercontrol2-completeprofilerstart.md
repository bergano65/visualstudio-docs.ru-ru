---
title: IActiveScriptProfilerControl2::CompleteProfilerStart | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b307352a3ba6d10ec3ae434536dee82d22504d33
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091290"
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