---
title: 'IActiveScriptErrorDebug110:: Жетексцептионсровнкинд | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug110::QueryIsFirstChance
ms.assetid: ecc16e54-93e4-4322-ae13-afa7cd860032
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d50ef1dfa3492fdc43a5010b624dae296c692722
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575055"
---
# <a name="iactivescripterrordebug110getexceptionthrownkind"></a>IActiveScriptErrorDebug110::GetExceptionThrownKind
Возвращает значение, показывающее вид созданного исключения.  
  
> [!IMPORTANT]
> [Интерфейс IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md) РЕАЛИЗОВАН в PDM версии 11,0 и выше. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetExceptionThrownKind(  
   SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND*  pExceptionKind  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pExceptionKind`  
 заполняет Тип создаваемого исключения (например, «First-вероятность» или «необработанное»), представленного значением перечисления [перечисления SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)