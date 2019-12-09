---
title: Константы СКРИПТСРЕАДИД | Документация Майкрософт
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
ms.openlocfilehash: bf1b23b191bda29b00bf29f482332301897f9f37
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575670"
---
# <a name="scriptthreadid-constants"></a>Константы SCRIPTTHREADID
Используется для указания типа потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Константы  
  
|постоянное значение.|Значение|Значение|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Выполняющийся в данный момент поток.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Базовый поток; то есть поток, в котором был создан экземпляр обработчика сценариев.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Все потоки.|  
  
## <a name="remarks"></a>Примечания  
 Тип `SCRIPTTHREADID` используется `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`и `IActiveScript::InterruptScriptThread`, но константы могут использоваться только `IActiveScript::GetScriptThreadState` и `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>См. также:  
 [IActiveScript:: жеткуррентскриптсреадид](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript:: жетскриптсреадид](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript:: жетскриптсреадстате](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)