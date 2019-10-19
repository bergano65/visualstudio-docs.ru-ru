---
title: Перечисление SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8eb089efbf608b488465809f997ffc82fc2c2e3c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574399"
---
# <a name="script_error_debug_exception_thrown_kind-enumeration"></a>Перечисление SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Задает вид создаваемого исключения. Это перечисление используется методом [IActiveScriptErrorDebug110:: жетексцептионсровнкинд](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) .  
  
> [!IMPORTANT]
> Эти константы реализованы в PDM версии 11.0 или более поздней. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Члены  
  
|Член|значения|Описание|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|Исключение является первичным.|  
|ETK_USER_UNHANDLED|0x00000001|Исключение не обработано в коде пользователя.|  
|ETK_UNHANDLED|0x00000002|Исключение не обработано в коде.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)