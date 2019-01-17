---
title: IActiveScript::GetScriptState | Документация Майкрософт
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
ms.openlocfilehash: a64067679e1c56831002494c579ffdeba84a1abe
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346635"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Возвращает текущее состояние обработчика сценариев. Этот метод может вызываться из потоков не основной не входили в выноске отличные от базовых объектов узла или [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) интерфейс.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pss`  
 [out] Адрес переменной, получающей значение, определенное в [перечисление SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md) перечисления. Значение указывает текущее состояние обработчика сценариев, связанных с вызывающего потока.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успешного выполнения или `E_POINTER` Если был указан недопустимый указатель.  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)