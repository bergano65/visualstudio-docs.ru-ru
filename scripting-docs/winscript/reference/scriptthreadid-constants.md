---
title: Константы SCRIPTTHREADID | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADID
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfbb39d10d552141a68d40a7be3f1715a80f8f57
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840209"
---
# <a name="scriptthreadid-constants"></a>Константы SCRIPTTHREADID
Используется для указания типа потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Константы  
  
|Константа|Значение|Значение|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Текущим выполняемым потоком.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Базовый поток; то есть был создан поток, в котором обработчик скриптов.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Все потоки.|  
  
## <a name="remarks"></a>Примечания  
 `SCRIPTTHREADID` Тип используется `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`, и `IActiveScript::InterruptScriptThread`, но констант может использоваться только с `IActiveScript::GetScriptThreadState` и `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>См. также  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)