---
title: IRemoteDebugApplication110::GetCurrentDebuggerOptions | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetCurrentDebuggerOptions
ms.assetid: a6e9cae1-e8f3-4d62-b133-52e9ca12ba7a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf49dcc7f49cfc98478514489ce67832bc397f53
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383363"
---
# <a name="iremotedebugapplication110getcurrentdebuggeroptions"></a>IRemoteDebugApplication110::GetCurrentDebuggerOptions
Возвращает набор параметров, которые в настоящее время включены.  
  
> [!IMPORTANT]
> [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md) является реализуется PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetCurrentDebuggerOptions([out] enum SCRIPT_DEBUGGER_OPTIONS* pCurrentOptions);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pCurrentOptions`  
 [out] Текущие параметры.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)   
 [Интерфейс IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)