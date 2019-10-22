---
title: 'IActiveScript:: Жетскриптстате | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d266e713879aafe1c5ca271d46b3030f3275460f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575728"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Извлекает текущее состояние обработчика скриптов. Этот метод может быть вызван из не базовых потоков, что приводит к небазовому вызову для размещения объектов или интерфейсу [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pss`  
 заполняет Адрес переменной, получающей значение, определенное в перечислении [перечисления скриптстате](../../winscript/reference/scriptstate-enumeration.md) . Значение указывает текущее состояние обработчика скриптов, связанного с вызывающим потоком.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успеха или `E_POINTER`, если был указан недопустимый указатель.  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)