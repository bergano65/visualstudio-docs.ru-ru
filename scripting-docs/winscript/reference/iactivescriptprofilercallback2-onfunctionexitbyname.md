---
title: 'IActiveScriptProfilerCallback2:: Онфунктионекситбинаме | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a70bc72dd1070759ad8b78e43926f06a2c56ec15
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571618"
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
Уведомляет объект профилировщика, что обработчик скриптов завершил выполнение вызова функции модель DOM (DOM).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>Параметры  
 `pwszFunctionName`  
 окне Имя функции, которую обработчик скриптов завершил выполнение.  
  
 `scriptType`  
 окне Тип функции. Описание допустимых значений см. в разделе [PROFILER_SCRIPT_TYPE enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемое значение этого метода игнорируется обработчиком скриптов.  
  
## <a name="remarks"></a>Заметки  
 Для вызовов DOM обработчик скриптов вызывает этот метод вместо вызова [IActiveScriptProfilerCallback:: онфунктионексит](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md). Это связано с большим количеством уникальных методов и свойств в модели DOM.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptProfilerCallback2:: онфунктионентербинаме](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)    
 [Интерфейс IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)