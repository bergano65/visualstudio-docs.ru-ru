---
title: IActiveScript::GetScriptState | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285a09308c7477dbeed68f9f93417b503ca4fe49
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640184"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Извлекает текущее состояние обработчика сценариев. Этот метод может вызываться из потоков, отличной от base не входили в системе счисления с основанием выноски объектов узла или [iactivescriptsite —](../../winscript/reference/iactivescriptsite.md) интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pss`  
 [out] Адрес переменной, которая получает значение, определенное в [перечисление SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md) перечисления. Значение указывает текущее состояние обработчика сценариев, связанных с вызывающего потока.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успешного выполнения или `E_POINTER` Если был указан недопустимый указатель.  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)