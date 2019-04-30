---
title: IActiveScriptProfilerCallback::OnFunctionEnter | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionEnter
apilocation:
- scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b8410fba08c1799d88532266c022d811c9553fd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993388"
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
Уведомляет объект профилировщика, который обработчик скриптов должен выполнить вызов функции, которая не является вызовом в объектной модели документа (DOM).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnFunctionEnter(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Параметры  
 `scriptId`  
 [in] Уникальный идентификатор сценария, который входит функция. Этот идентификатор назначается обработчик скриптов.  
  
 `functionId`  
 [in] Уникальный идентификатор функции. Этот идентификатор назначается обработчик скриптов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемое значение этого метода обрабатывается обработчиком сценариев.  
  
## <a name="remarks"></a>Примечания  
 Для вызовов DOM, обработчик скриптов вызывает [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) вместо `IActiveScriptProfilerCallback::OnFunctionEnter`. Это происходит из-за большого количества уникальных методы и свойства в модели DOM.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)