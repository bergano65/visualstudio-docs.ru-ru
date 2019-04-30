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
ms.openlocfilehash: 404d3939e0a328beb5e2413d25885fddf8478ead
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443649"
---
# <a name="scriptdebuggeroptions-enumeration"></a>Перечисление SCRIPT_DEBUGGER_OPTIONS
Указывает набор параметров и/или возможности, которые применяются к подключенному отладчику. Используется в [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) и [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
> Эти константы реализованы в PDM v10.0 и больше. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>Участники  
  
|Член|Значение|Описание|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|Параметры не заданы.|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|Указывает, что время выполнения скрипта должны создавать события BREAKREASON_ERROR, когда возникает исключение. Этот параметр может быть устанавливаемых отладчиком, или пользовательского кода с помощью `Debug.enableFirstChanceExceptions(<true&#124;false>)`.|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|Указывает, что присоединенному отладчику поддерживает рабочие роли.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)