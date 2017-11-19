---
title: "IActiveScriptProfilerControl2::PrepareProfilerStop | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerControl2::PrepareProfilerStop
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78078cd874be1d7d3d169be2d3d70e65866be3fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Уведомляет профилировщик о том, что вы собираетесь остановить профилирование на всех применимых обработчиков сценариев. С помощью этого метода, можно получить полный стек вызовов, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется при остановке профилирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Параметры  
 Метод не принимает никаких параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение HRESULT. Ниже приведены возможные значения.  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Профилирование не удалось запустить.|  
|`S_FALSE`|Профилирование была остановлена, если скрипт не был запущен.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Профилирование не включен.|  
  
## <a name="remarks"></a>Примечания  
 Вызов `IActiveScriptProfilerControl2::PrepareProfilerStop` гарантирует, что отправка событий для функций в стеке вызовов. Этот метод должен вызываться перед остановкой профилирования на любой обработчик скриптов, который находится на текущей вкладке. Метод может вызываться для любой обработчик скриптов.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [Интерфейс IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)