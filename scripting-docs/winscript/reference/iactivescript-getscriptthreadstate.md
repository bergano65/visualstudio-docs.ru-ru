---
title: "IActiveScript::GetScriptThreadState | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetScriptThreadState
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b11b8566857bc70aaeac5bdf8e8e357fa5d9c2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Извлекает текущее состояние потока сценария.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `stidThread`  
 [in] Идентификатор потока, для которого требуется состояние или один из следующих идентификаторов специальные потока:  
  
|Значение|Значение|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Базовый поток; то есть был создан поток, в котором модуль создания скриптов.|  
|SCRIPTTHREADID_CURRENT|Текущий выполняемый поток.|  
  
 `pstsState`  
 [out] Адрес переменной, которая получает состояние указанного потока. Состояние указывается один из именованных констант значений, определенных в [перечисление SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md) перечисления. Если этот параметр не определить текущий поток, состояние может измениться в любое время.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидалось (например, обработчик сценариев еще не загрузки или инициализации).|  
  
## <a name="remarks"></a>Примечания  
 Этот метод может вызываться из потоков, отличной от base не входили в системе счисления с основанием выноски объектов узла или [iactivescriptsite —](../../winscript/reference/iactivescriptsite.md) интерфейса.  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)