---
title: IActiveScript::SetScriptState | Документация Майкрософт
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
ms.openlocfilehash: 16a13b545ddd482f8aa143d289d46447370e23ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935535"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Помещает обработчик скриптов в заданном состоянии. Этот метод может вызываться из потоков не основной не входили в выноске отличные от базовых объектов узла или [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) интерфейс.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
|`E_FAIL`|Обработчик скриптов не поддерживает переход обратно в исходное состояние. Узел должен отменить этот обработчик скриптов и создание, инициализация и загрузить новый обработчик сценариев для достижения такого же эффекта.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов еще не была загрузки или инициализации) и поэтому не удалось.|  
|`OLESCRIPT_S_PENDING`|Метод был поставлен в очередь успешно, но состояние еще не изменился. Когда изменения состояния, сайт будет вызван обратно через [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) метод.|  
|`S_FALSE`|Метод выполнен успешно, но он уже был в указанном состоянии.|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о создании сценариев состояния обработчика см. в разделе состояния обработчика скриптов [обработчики скриптов Windows](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>См. также  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)