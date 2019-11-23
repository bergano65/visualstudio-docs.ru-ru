---
title: IActiveScriptProfilerControl2::P Репарепрофилерстоп | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::PrepareProfilerStop
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24d4d73e0263882ad028ea66d3fac5e24f3af9ba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571442"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Уведомляет профилировщик о том, что вы собираетесь отключить профилирование для всех применимых обработчиков скриптов. С помощью этого метода можно получить полный стек вызовов, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется, когда вы останавливаете профилирование.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Параметры  
 Метод не принимает никаких параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение HRESULT. Ниже приведены возможные значения.  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Не удалось запустить профилирование.|  
|`S_FALSE`|Профилирование было остановлено, когда сценарий не выполнялся.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Профилирование не включено.|  
  
## <a name="remarks"></a>Примечания  
 Вызов `IActiveScriptProfilerControl2::PrepareProfilerStop` гарантирует отправку событий для функций в стеке вызовов. Этот метод должен быть вызван перед остановкой профилирования на любом обработчике скриптов, который находится на текущей вкладке. Метод может быть вызван для любого обработчика скриптов.  
  
## <a name="see-also"></a>См. также:  
 [IActiveScriptProfilerControl2:: комплетепрофилерстарт](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [Интерфейс IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)