---
title: "IActiveScript::SetScriptSite | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.SetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_SetScriptSite
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11fa9003abb03c42adcbf3a548bb5b90d763a344
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Уведомляет обработчик скриптов для [iactivescriptsite —](../../winscript/reference/iactivescriptsite.md) сайта интерфейс, предоставленный средой размещения. Этот метод перед любыми другими [IActiveScript](../../winscript/reference/iactivescript.md) используется методов интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pScriptSite`  
 [in] Адрес узла предоставленный скрипт узла, который будет связан с этим экземпляром обработчика скриптов. Сайт должен однозначно назначаются данного сценария экземпляра ядра; его нельзя использовать совместно с другими обработчиков сценариев.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_FAIL`|Произошла неизвестная ошибка; Обработчик скриптов не удалось завершить инициализацию на сайте.|  
|`E_INVALIDARG`|Недопустимый аргумент.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидалось (например, сайт уже было задано).|  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)