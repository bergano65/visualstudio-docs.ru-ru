---
title: 'IActiveScript:: Жетскриптсреадид | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a0fb1eebfcb6ed100056289fab6bce662f86a7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575707"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Извлекает идентификатор, определенный ядром сценариев, для потока, связанного с данным потоком Win32.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwWin32ThreadID` ,  
 окне Идентификатор потока выполняющегося потока Win32 в текущем процессе. Используйте функцию [IActiveScript:: жеткуррентскриптсреадид](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) , чтобы получить идентификатор потока выполняющегося в данный момент потока.  
  
 `pstidThread` ,  
 заполняет Адрес переменной, получающей идентификатор потока скрипта, связанный с заданным потоком Win32. Интерпретация этого идентификатора оставлена обработчику скриптов, но может быть просто копией идентификатора потока Windows. Обратите внимание, что при завершении потока Win32 этот идентификатор будет неназначенным и впоследствии может быть назначен другому потоку.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Смысл|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов еще не загружен или не инициализирован) и поэтому завершился ошибкой.|  
  
## <a name="remarks"></a>Заметки  
 Полученный идентификатор можно использовать при последующих вызовах методов управления выполнением потока скриптов, таких как метод [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
 Этот метод может быть вызван из не базовых потоков, что приводит к небазовому вызову для размещения объектов или интерфейсу [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)