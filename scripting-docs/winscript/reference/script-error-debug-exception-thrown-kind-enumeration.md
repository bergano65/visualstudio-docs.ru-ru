---
title: Перечисление SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 997c5149467591a7612e6ff10b0efcc3efbc91bf
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087806"
---
# <a name="scripterrordebugexceptionthrownkind-enumeration"></a>Перечисление SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Задает вид создаваемого исключения. Это перечисление используется с [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) метод.  
  
> [!IMPORTANT]
>  Эти константы реализованы в PDM версии 11.0 или более поздней. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Члены  
  
|Член|Значение|Описание:|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|Исключение является первичным.|  
|ETK_USER_UNHANDLED|0x00000001|Исключение не обработано в коде пользователя.|  
|ETK_UNHANDLED|0x00000002|Исключение не обработано в коде.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)