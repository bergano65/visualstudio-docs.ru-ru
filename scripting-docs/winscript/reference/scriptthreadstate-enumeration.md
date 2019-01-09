---
title: Перечисление SCRIPTTHREADSTATE | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c66d078effd510b3f64cf1f443926984ff2e282
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094124"
---
# <a name="scriptthreadstate-enumeration"></a>Перечисление SCRIPTTHREADSTATE
Указывает состояние потока в обработчик сценариев. Это перечисление используется с [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Значения перечисления  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|Указанный поток в настоящее время не обслуживания событием сценария, немедленно выполняется обработка текста скрипта, или макрос скрипта.|  
|SCRIPTTHREADSTATE_RUNNING|Указанный поток активно обслуживания событием сценария, немедленно выполняется обработка текста скрипта, или макрос скрипта.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и коды ошибок активных скриптов](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)