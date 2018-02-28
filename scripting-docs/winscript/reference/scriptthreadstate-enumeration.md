---
title: "Перечисление SCRIPTTHREADSTATE | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- SCRIPTTHREADSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e18cc6f5f2afb1dcea6835983f69f6a6f7b9280
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="scriptthreadstate-enumeration"></a>Перечисление SCRIPTTHREADSTATE
Указывает состояние потока в обработчик сценариев. Это перечисление используется методом [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Значения перечисления  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|Указанный поток в настоящее время не обслуживания сценариев событий, текст сценария обработки немедленно выполняется, или используется макрос сценария.|  
|SCRIPTTHREADSTATE_RUNNING|Указанный поток активно обслуживания сценариев событий, текст сценария обработки немедленно выполняется, или используется макрос скрипта.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и коды ошибок активных скриптов](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)