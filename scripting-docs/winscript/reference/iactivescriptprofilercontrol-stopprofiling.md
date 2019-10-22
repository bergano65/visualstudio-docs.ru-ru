---
title: 'IActiveScriptProfilerControl:: Стоппрофилинг | Документация Майкрософт'
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
ms.openlocfilehash: da5900678093d57b3c995ac3bca8464ccd612fb2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571551"
---
# <a name="iactivescriptprofilercontrolstopprofiling"></a>IActiveScriptProfilerControl::StopProfiling
Останавливает профилирование в обработчике скриптов. Этот метод вызывает [IActiveScriptProfilerCallback:: Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) в объекте профилировщика, а затем освобождает его.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT StopProfiling(  
    [in] HRESULT hrShutdownReason);  
```  
  
#### <a name="parameters"></a>Параметры  
 `hrShutdownReason`  
 окне Значение HRESULT, передаваемое в качестве параметра методу [IActiveScriptProfilerCallback:: Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) объекта профилировщика.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение HRESULT. Ниже приведены возможные значения.  
  
|Возвращаемое значение|Смысл|  
|------------------|-------------|  
|`S_OK`|Метод успешно выполнен.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Профилирование не включено.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)