---
title: 'IActiveScript:: Жетскриптсреадстате | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 38f6ef4b0acdf6e3b746316bef8abe9a3f0f8225
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578007"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Извлекает текущее состояние потока скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `stidThread`  
 окне Идентификатор потока, для которого требуется состояние, или один из следующих специальных идентификаторов потока:  
  
|значения|Смысл|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Базовый поток; то есть поток, в котором был создан экземпляр обработчика сценариев.|  
|SCRIPTTHREADID_CURRENT|Выполняющийся в данный момент поток.|  
  
 `pstsState`  
 заполняет Адрес переменной, которая получает состояние указанного потока. Состояние обозначается одним из именованных постоянных значений, определяемых перечислением [перечисления скриптсреадстате](../../winscript/reference/scriptthreadstate-enumeration.md) . Если этот параметр не определяет текущий поток, состояние может измениться в любое время.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Смысл|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов еще не загружен или не инициализирован).|  
  
## <a name="remarks"></a>Заметки  
 Этот метод может быть вызван из не базовых потоков, что приводит к небазовому вызову для размещения объектов или интерфейсу [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)