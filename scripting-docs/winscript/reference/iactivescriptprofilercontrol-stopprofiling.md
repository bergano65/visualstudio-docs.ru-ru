---
title: IActiveScriptProfilerControl::StopProfiling | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StopProfiling
apilocation:
- scrobj.dll
ms.assetid: 23b46ed6-a398-44c0-bc49-bf122e697cfe
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 750693db9aa809e6b3521f0312cebcf45d8d720d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993012"
---
# <a name="iactivescriptprofilercontrolstopprofiling"></a>IActiveScriptProfilerControl::StopProfiling
Останавливает профилирование на обработчик скриптов. Этот метод вызывает метод [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) на объект профилировщика и освобождает его.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT StopProfiling(  
    [in] HRESULT hrShutdownReason);  
```  
  
#### <a name="parameters"></a>Параметры  
 `hrShutdownReason`  
 [in] HRESULT передается как параметр [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) метод объекта профилировщика.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение HRESULT. Ниже приведены возможные значения.  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Метод успешно выполнен.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Профилирование не включено.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)