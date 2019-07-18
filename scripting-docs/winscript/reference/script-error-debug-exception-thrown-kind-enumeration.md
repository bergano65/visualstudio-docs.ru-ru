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
ms.openlocfilehash: 3be6989195eacdd4d70bd13790d55e4f6cfc769d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443642"
---
# <a name="scripterrordebugexceptionthrownkind-enumeration"></a>Перечисление SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Задает вид создаваемого исключения. Это перечисление используется с [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) метод.  
  
> [!IMPORTANT]
> Эти константы реализованы в PDM версии 11.0 или более поздней. Обнаружено в activdbg100.h.  
  
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