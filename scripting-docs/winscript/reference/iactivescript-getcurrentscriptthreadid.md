---
title: "IActiveScript::GetCurrentScriptThreadID | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetCurrentScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5921dc4d0f9a9bf0d505fece0f47354cb16d440c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Извлекает определенный сценариев ядра-идентификатор для текущего потока. Идентификатор может использоваться в последующих вызовах методов управление выполнением скриптов поток например [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstidThread`  
 [out] Адрес переменной, которая получает идентификатор потока скрипт, связанный с текущим потоком. Интерпретация этого идентификатора определяется для обработчика скриптов, но может быть копию идентификатор потока Windows. Если завершения потока Win32, этот идентификатор становится неназначенные и впоследствии могут быть назначены другой поток.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успешного выполнения или `E_POINTER` Если был указан недопустимый указатель.  
  
## <a name="remarks"></a>Примечания  
 Этот метод может вызываться из потоков, отличной от base не входили в системе счисления с основанием выноски объектов узла или [iactivescriptsite —](../../winscript/reference/iactivescriptsite.md) интерфейса.  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)