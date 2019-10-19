---
title: Перечисление SCRIPT_DEBUGGER_OPTIONS | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SCRIPT_DEBUGGER_OPTIONS Enumeration
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c69d419732786442cda275bf85c74ab2b9d3e870
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574567"
---
# <a name="script_debugger_options-enumeration"></a>Перечисление SCRIPT_DEBUGGER_OPTIONS
Указывает набор параметров и/или возможностей, которые применяются к подключенному отладчику. Используется в [IDebugApplicationNode100:: жетексклудеддокументс](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) и [IDebugApplicationNode100:: сетфилтерфоревентсинк](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
> Эти константы реализуются с помощью PDM v 10.0 и более поздних версий. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>Члены  
  
|Член|значения|Описание|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|Параметры не заданы.|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|Указывает, что среда выполнения скрипта должна вызывать события BREAKREASON_ERROR при возникновении исключения. Этот параметр может быть задан отладчиком или задан пользовательским кодом через `Debug.enableFirstChanceExceptions(<true&#124;false>)`.|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|Указывает, что подключенный отладчик поддерживает рабочие веб-процессы.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)