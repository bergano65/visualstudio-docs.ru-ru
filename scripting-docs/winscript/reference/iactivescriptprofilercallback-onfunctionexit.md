---
title: 'IActiveScriptProfilerCallback:: Онфунктионексит | Документация Майкрософт'
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
ms.openlocfilehash: 87801b7873e43498031264ff4719fb47eca99f40
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571678"
---
# <a name="iactivescriptprofilercallbackonfunctionexit"></a>IActiveScriptProfilerCallback::OnFunctionExit
Уведомляет объект профилировщика, что обработчик скриптов завершил выполнение вызова функции, который не является вызовом модель DOM (DOM).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnFunctionExit(  
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
  
## <a name="remarks"></a>Заметки  
 Для вызовов DOM обработчик скриптов вызывает [IActiveScriptProfilerCallback2:: онфунктионекситбинаме](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) вместо `IActiveScriptProfilerCallback::OnFunctionExit`. Это связано с большим количеством уникальных методов и свойств в модели DOM.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptProfilerCallback:: онфунктионентер](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)    
 [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)