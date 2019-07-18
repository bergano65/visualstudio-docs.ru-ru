---
title: IActiveScriptProfilerCallback2::OnFunctionEnterByName | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionEnterByName
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6fdb4addace1b0bbabdd4303c3943b976763514
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993271"
---
# <a name="iactivescriptprofilercallback2onfunctionenterbyname"></a>IActiveScriptProfilerCallback2::OnFunctionEnterByName
Уведомляет объект профилировщика, обработчик сценариев будет выполнен вызов функции объектной модели документа (DOM).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pwszFunctionName`  
 [in] Имя функции, будет выполнен обработчика скриптов.  
  
 `scriptType`  
 [in] Тип функции. Описание допустимых значений, см. в разделе [перечисление PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемое значение этого метода обрабатывается обработчиком сценариев.  
  
## <a name="remarks"></a>Примечания  
 Для вызовов DOM, обработчик скриптов вызывает этот метод вместо вызова метода [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md). Это происходит из-за большого количества уникальных методы и свойства в модели DOM.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [Интерфейс IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)