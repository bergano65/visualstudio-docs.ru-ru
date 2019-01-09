---
title: IActiveScript::GetScriptThreadState | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b191f1b70aa522cba0a04e0781ada69a8fe5ca5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097530"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Возвращает текущее состояние потока скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `stidThread`  
 [in] Идентификатор потока, для которого требуется состояние или один из следующих идентификаторов специальный поток:  
  
|Значение|Значение|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Базовый поток; то есть был создан поток, в котором обработчик скриптов.|  
|SCRIPTTHREADID_CURRENT|Текущим выполняемым потоком.|  
  
 `pstsState`  
 [out] Адрес переменной, которая получает состояние указанного потока. Состояние обозначается один из именованных значения констант, определенных по [перечисление SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md) перечисления. Если этот параметр не идентифицирует текущий поток, состояние может измениться в любое время.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов еще не была загрузки или инициализации).|  
  
## <a name="remarks"></a>Примечания  
 Этот метод может вызываться из потоков не основной не входили в выноске отличные от базовых объектов узла или [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) интерфейс.  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)