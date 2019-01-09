---
title: Константы SCRIPTTHREADID | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 27852f97cf0a78919b10043c64b1c5a7cc7d3ec5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097816"
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