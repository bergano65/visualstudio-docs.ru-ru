---
title: "IActiveScriptProfilerCallback::Initialize | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.Initialize
apilocation: scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82e599ae94f422352706a0ec6cd9387bfa6799f2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackinitialize"></a>IActiveScriptProfilerCallback::Initialize
Вызывается для инициализации объекта профилировщика при каждом запуске профилирования на обработчик скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwContext`  
 [in] 4-байтовое значение, передаваемое [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение HRESULT. Ниже приведены возможные значения.  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Если метод не удается инициализировать объект профилировщика, он должен возвращать значение HRESULT для уведомления обработчика скриптов. В этом случае обработчик скриптов должны напрямую вызывать [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md), передавая параметр HRESULT, а затем отпустите объекта профилировщика.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)