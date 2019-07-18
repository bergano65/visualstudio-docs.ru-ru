---
title: IActiveScriptProfilerCallback::Shutdown | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Shutdown
apilocation:
- scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 091ccc30f16081fdca8f10778efec208ef5ccb16
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993427"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Вызывается для информирования объекта профилировщика, каждый раз, когда профилирование останавливается на обработчик скриптов. Таким образом, объект профилировщика можно вызвать его процедуры очистки, при необходимости. Этот метод также вызывается обработчиком сценариев, завершении работы обработчика скриптов, или при вызове [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) завершается ошибкой.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Параметры  
 `hrReason`  
 [in] Причина завершения работы. Если обработчик скриптов завершает работу, `S_OK` передается. Если вызов [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) возвращает ошибку HRESULT, передается значение HRESULT. В противном случае это значение извлекается из [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемое значение этого метода обрабатывается обработчиком сценариев.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)