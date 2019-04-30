---
title: IActiveScriptProfilerCallback::OnFunctionExit | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionExit
apilocation:
- scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c84b64a12b1a6b61399f70b7209c86dd8d2a9a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993336"
---
# <a name="iactivescriptprofilercallbackonfunctionexit"></a>IActiveScriptProfilerCallback::OnFunctionExit
Уведомляет профилировщик, что объект, чтобы вызывать по завершении выполнения функции обработчика скриптов, не является вызов в объектной модели документа (DOM).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnFunctionExit(  
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
 Для вызовов DOM, обработчик скриптов вызывает [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) вместо `IActiveScriptProfilerCallback::OnFunctionExit`. Это происходит из-за большого количества уникальных методы и свойства в модели DOM.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)   
 [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)