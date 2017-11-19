---
title: "Перечисление SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6fe5b308ea75956d9e5826b4daadaef3a823141f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="scripterrordebugexceptionthrownkind-enumeration"></a>Перечисление SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Задает вид создаваемого исключения. Это перечисление используется методом [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) метод.  
  
> [!IMPORTANT]
>  Эти константы реализованы в PDM версии 11.0 или более поздней. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Члены  
  
|Член|Значение|Описание|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|Исключение является первичным.|  
|ETK_USER_UNHANDLED|0x00000001|Исключение не обработано в коде пользователя.|  
|ETK_UNHANDLED|0x00000002|Исключение не обработано в коде.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)