---
title: IActiveScriptProfilerCallback2::OnFunctionExitByName | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionExitByName
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb198f56e5ff73561fe7b42a25b019dfb0e3817c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094566"
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
Уведомляет профилировщик, что объект, который обработчик скриптов завершила выполнение вызова функции объектной модели документа (DOM).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>Параметры  
 `pwszFunctionName`  
 [in] Имя функции, что обработчик сценариев завершения работы.  
  
 `scriptType`  
 [in] Тип функции. Описание допустимых значений, см. в разделе [перечисление PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемое значение этого метода обрабатывается обработчиком сценариев.  
  
## <a name="remarks"></a>Примечания  
 Для вызовов DOM, обработчик скриптов вызывает этот метод вместо вызова метода [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md). Это происходит из-за большого количества уникальных методы и свойства в модели DOM.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [Интерфейс IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)