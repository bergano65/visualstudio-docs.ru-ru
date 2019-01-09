---
title: IActiveScriptProfilerControl2::PrepareProfilerStop | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 086ec8b4a126c65162638afde4d8081269757e1c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089522"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Уведомляет профилировщик, что вы собираетесь остановить профилирование на всех применимых обработчиков сценариев. С помощью этого метода, можно получить полный стек вызовов, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется при остановке профилирования.  
  
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
|`S_FALSE`|Профилирование было остановлено, если скрипт не был запущен.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Профилирование не включено.|  
  
## <a name="remarks"></a>Примечания  
 Вызов `IActiveScriptProfilerControl2::PrepareProfilerStop` гарантирует отправку событий для функций в стеке вызовов. Этот метод должен вызываться перед остановкой профилирования на любой обработчик скриптов, который находится на текущей вкладке. Метод может вызываться для любого обработчика скриптов.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [Интерфейс IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)