---
title: 'IActiveScript:: SetScriptState | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea947e00ffd5a3498261f4a3a8acd4791e8ace60
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577993"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Помещает обработчик скриптов в заданное состояние. Этот метод может быть вызван из не базовых потоков, что приводит к небазовому вызову для размещения объектов или интерфейсу [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ss`  
 окне Устанавливает обработчик скриптов в заданное состояние. Может быть одним из значений, определенных в перечислении [перечисления скриптстате](../../winscript/reference/scriptstate-enumeration.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Смысл|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_FAIL`|Обработчик скриптов не поддерживает переход обратно в инициализированное состояние. Узел должен отбросить этот обработчик скриптов и создать, инициализировать и загрузить новый обработчик скриптов для достижения того же результата.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов еще не загружен или не инициализирован) и поэтому завершился ошибкой.|  
|`OLESCRIPT_S_PENDING`|Метод был успешно поставлен в очередь, но состояние еще не изменилось. При изменении состояния сайт будет вызываться обратно с помощью метода [IActiveScriptSite:: онстатечанже](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|Метод выполнен успешно, но скрипт уже находится в заданном состоянии.|  
  
## <a name="remarks"></a>Заметки  
 Дополнительные сведения о состоянии обработчика скриптов см. в разделе состояния обработчика сценариев в [обработчиках сценариев Windows](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>См. также  
 [IActiveScript:: Clone](../../winscript/reference/iactivescript-clone.md)    
 [IActiveScript:: жетскриптдиспатч](../../winscript/reference/iactivescript-getscriptdispatch.md)    
 [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)    
 [IActiveScriptParse::P арсескрипттекст](../../winscript/reference/iactivescriptparse-parsescripttext.md)    
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)