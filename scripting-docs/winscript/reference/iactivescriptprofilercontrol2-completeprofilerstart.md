---
title: IActiveScriptProfilerControl2::CompleteProfilerStart | Документы Microsoft
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
ms.openlocfilehash: 5abd4ee4237991714bfe3d8ba21b083f1a1920cd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724504"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Уведомляет профилировщик, что вы запустили профилирования на всех применимых обработчиков сценариев. С помощью этого метода, можно получить полный стек вызовов, если [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выполняется при запуске профилирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Параметры  
 Метод не принимает никаких параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение HRESULT. Ниже приведены возможные значения.  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Не удается запустить профилирование.|  
|`S_FALSE`|Профилирование был запущен, если скрипт не был запущен.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Профилирование не включен. Обратный вызов не был установлен.|  
|`E_OUTOFMEMORY`|Не удается получить стек вызовов из-за условия нехватки памяти.|  
  
## <a name="remarks"></a>Примечания  
 Вызов `IActiveScriptProfilerControl2::CompleteProfilerStart` гарантирует, что отправляются события для функции, уже находится в стеке вызовов. Этот метод должен вызываться после профилирования запускается на любой обработчик скриптов, который находится на текущей вкладке. Метод может вызываться для любой обработчик скриптов.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [Интерфейс IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)