---
title: "IActiveScript::SetScriptState | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.SetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 146cd5e4f2b6137fc6fe6e32e8ca153c3aab8fd5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Помещает обработчик скриптов в указанном состоянии. Этот метод может вызываться из потоков, отличной от base не входили в системе счисления с основанием выноски объектов узла или [iactivescriptsite —](../../winscript/reference/iactivescriptsite.md) интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ss`  
 [in] Задает обработчик скриптов в указанное состояние. Может принимать одно из значений, определенных в [перечисление SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md) перечисления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_FAIL`|Обработчик скриптов не поддерживает переход обратно в исходное состояние. Имя узла необходимо отменить этот обработчик скриптов и создать, инициализировать и загрузить новый обработчик сценариев для достижения такого же эффекта.|  
|`E_UNEXPECTED`|Вызов не ожидалось (например, обработчик сценариев еще не загрузки или инициализации) и поэтому не удалось выполнить.|  
|`OLESCRIPT_S_PENDING`|Метод в очередь и успешно, но состояние еще не изменилась. При изменения состояния, узел получит обратный вызов через [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) метод.|  
|`S_FALSE`|Метод успешно выполнен, но скрипт уже был в указанном состоянии.|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о сценариях engine состояний см. разделе состояний обработчика сценария [обработчики скриптов Windows](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>См. также  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)