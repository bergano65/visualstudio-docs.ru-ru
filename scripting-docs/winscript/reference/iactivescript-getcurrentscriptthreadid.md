---
title: IActiveScript::GetCurrentScriptThreadID | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e1b6e7bae7d78c18e11cd1aac8d0844fb9e90a5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935660"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Извлекает определенный сценариев ядра-идентификатор для текущего потока. Идентификатор может использоваться в последующих вызовах методов управление выполнением скриптов поток например [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstidThread`  
 [out] Адрес переменной, которая получает идентификатор потока сценарий, связанный с текущим потоком. Интерпретация этого идентификатора остается на обработчик скриптов, но это может быть просто копию идентификатор потока Windows. Если поток Win32 завершился, этот идентификатор становится неназначенные и впоследствии могут быть назначены другим потоком.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успешного выполнения или `E_POINTER` Если был указан недопустимый указатель.  
  
## <a name="remarks"></a>Примечания  
 Этот метод может вызываться из потоков не основной не входили в выноске отличные от базовых объектов узла или [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) интерфейс.  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)