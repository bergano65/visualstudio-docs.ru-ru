---
title: 'IActiveScriptProfilerCallback:: Онфунктионентер | Документация Майкрософт'
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
ms.openlocfilehash: 6157638353712d6f376fa1eb46a68980b493a5c3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571682"
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
Уведомляет объект профилировщика о том, что обработчик скриптов собирается выполнить вызов функции, который не является вызовом модель DOM (DOM).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnFunctionEnter(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Параметры  
 `scriptId`  
 окне Уникальный идентификатор скрипта, частью которого является функция. Этот идентификатор назначается обработчиком скриптов.  
  
 `functionId`  
 окне Уникальный идентификатор функции. Этот идентификатор назначается обработчиком скриптов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемое значение этого метода игнорируется обработчиком скриптов.  
  
## <a name="remarks"></a>Примечания  
 Для вызовов DOM обработчик скриптов вызывает [IActiveScriptProfilerCallback2:: онфунктионентербинаме](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) вместо `IActiveScriptProfilerCallback::OnFunctionEnter`. Это связано с большим количеством уникальных методов и свойств в модели DOM.  
  
## <a name="see-also"></a>См. также:  
 [IActiveScriptProfilerCallback:: онфунктионексит](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)