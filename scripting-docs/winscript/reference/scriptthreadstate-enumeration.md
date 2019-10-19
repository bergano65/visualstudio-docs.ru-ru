---
title: Перечисление СКРИПТСРЕАДСТАТЕ | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: bc4ef840310c27ccbadce2ed4f632514b555ef98
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575653"
---
# <a name="scriptthreadstate-enumeration"></a>Перечисление SCRIPTTHREADSTATE
Указывает состояние потока в обработчике скриптов. Это перечисление используется методом [IActiveScript:: жетскриптсреадстате](../../winscript/reference/iactivescript-getscriptthreadstate.md) .  
  
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
|SCRIPTTHREADSTATE_NOTINSCRIPT|Указанный поток в настоящее время не обслуживает событие в скрипте, обрабатывает немедленно выполняемый текст сценария или запускает макрос скрипта.|  
|SCRIPTTHREADSTATE_RUNNING|Указанный поток активно обслуживает событие в скрипте, обрабатывает немедленно выполняемый текст сценария или запускает макрос скрипта.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и коды ошибок активных скриптов](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)