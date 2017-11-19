---
title: "IActiveScript::GetScriptThreadID | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8850319035b7b5e3a9cbbd4bbe4340e1eefacc96
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Извлекает определенный сценариев ядра-идентификатор потока, связанного с данной потоком Win32.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwWin32ThreadID` ,  
 [in] Идентификатор потока выполняющийся поток Win32 в текущем процессе. Используйте [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) функции, чтобы получить идентификатор текущего потока.  
  
 `pstidThread` ,  
 [out] Адрес переменной, которая получает идентификатор потока скрипт, связанный с данной потоком Win32. Интерпретация этого идентификатора определяется для обработчика скриптов, но может быть копию идентификатор потока Windows. Обратите внимание, что если завершения потока Win32, этот идентификатор становится неназначенные впоследствии может быть назначен другому потоку.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидалось (например, обработчик сценариев еще не загрузки или инициализации) и поэтому не удалось выполнить.|  
  
## <a name="remarks"></a>Примечания  
 Полученный идентификатор может использоваться в последующих вызовах методов управления сценария потока выполнения таких как [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) метод.  
  
 Этот метод может вызываться из потоков, отличной от base не входили в системе счисления с основанием выноски объектов узла или [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) интерфейса.  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)