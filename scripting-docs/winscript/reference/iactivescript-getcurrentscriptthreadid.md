---
title: 'IActiveScript:: Жеткуррентскриптсреадид | Документация Майкрософт'
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
ms.openlocfilehash: dedb16e0c007ed05370fb54835f84f00784c1ae4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575767"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Извлекает идентификатор, определяемый обработчиком сценариев, для выполняющегося в данный момент потока. Идентификатор можно использовать при последующих вызовах методов управления выполнением потока скриптов, таких как метод [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstidThread`  
 заполняет Адрес переменной, которая получает идентификатор потока скрипта, связанный с текущим потоком. Интерпретация этого идентификатора оставлена обработчику скриптов, но может быть просто копией идентификатора потока Windows. Если поток Win32 завершается, этот идентификатор преобразуется в неназначенный и затем может быть назначен другому потоку.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успеха или `E_POINTER`, если был указан недопустимый указатель.  
  
## <a name="remarks"></a>Заметки  
 Этот метод может быть вызван из не базовых потоков, что приводит к небазовому вызову для размещения объектов или интерфейсу [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)