---
title: 'IRemoteDebugApplication110:: Сетдебугжероптионс | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::SetDebuggerOptions
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7168a4ef8ec70368c0ff691ba1f721275f9d65d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577424"
---
# <a name="iremotedebugapplication110setdebuggeroptions"></a>IRemoteDebugApplication110::SetDebuggerOptions
Вызывается для обновления параметров отладчика. Этот метод должен вызываться после [IRemoteDebugApplication:: коннектдебугжер](../../winscript/reference/iremotedebugapplication-connectdebugger.md). Метод [IRemoteDebugApplication::D исконнектдебугжер](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) автоматически сбрасывается в параметры по умолчанию. По умолчанию параметр имеет значение 0 (SDO_NONE).  
  
> [!IMPORTANT]
> [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md) реализуется с помощью PDM v 11.0 и более поздних версий. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetDebuggerOptions(        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,        [in] enum SCRIPT_DEBUGGER_OPTIONS value    );  
```  
  
#### <a name="parameters"></a>Параметры  
 `mask`  
 Маска [перечисления SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md) .  
  
 `value`  
 Значение [перечисления SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md) .  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)  
 [Интерфейс IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)