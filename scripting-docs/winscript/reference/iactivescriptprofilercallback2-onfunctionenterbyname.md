---
title: 'IActiveScriptProfilerCallback2:: Онфунктионентербинаме | Документация Майкрософт'
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
ms.openlocfilehash: c0407441c77250b2cc27e9fee09c5039bb8e44ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571637"
---
# <a name="iactivescriptprofilercallback2onfunctionenterbyname"></a>IActiveScriptProfilerCallback2::OnFunctionEnterByName
Уведомляет объект профилировщика, что обработчик скриптов будет выполнять вызов функции модель DOM (DOM).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pwszFunctionName`  
 окне Имя функции, которую будет выполнять обработчик скриптов.  
  
 `scriptType`  
 окне Тип функции. Описание допустимых значений см. в разделе [Перечисление PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемое значение этого метода игнорируется обработчиком скриптов.  
  
## <a name="remarks"></a>Примечания  
 Для вызовов DOM обработчик скриптов вызывает этот метод вместо вызова [IActiveScriptProfilerCallback:: онфунктионентер](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md). Это связано с большим количеством уникальных методов и свойств в модели DOM.  
  
## <a name="see-also"></a>См. также:  
 [IActiveScriptProfilerCallback2:: онфунктионекситбинаме](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [Интерфейс IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)