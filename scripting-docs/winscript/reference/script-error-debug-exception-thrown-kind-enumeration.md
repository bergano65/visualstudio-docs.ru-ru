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
ms.openlocfilehash: b9dae0161e3337411a56e316e04cf467a1f05e6a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155723"
---
# <a name="scripterrordebugexceptionthrownkind-enumeration"></a>Перечисление SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Задает вид создаваемого исключения. Это перечисление используется с [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) метод.  
  
> [!IMPORTANT]
>  Эти константы реализованы в PDM версии 11.0 или более поздней. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Участники  
  
|Член|Значение|Описание|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|Исключение является первичным.|  
|ETK_USER_UNHANDLED|0x00000001|Исключение не обработано в коде пользователя.|  
|ETK_UNHANDLED|0x00000002|Исключение не обработано в коде.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)