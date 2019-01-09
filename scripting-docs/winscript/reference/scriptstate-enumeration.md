---
title: Перечисление SCRIPTSTATE | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff935e54e42eef6691948a7e0d91a495c5153adc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097803"
---
# <a name="scriptstate-enumeration"></a>Перечисление SCRIPTSTATE
Задает состояние обработчика сценариев. Это перечисление используется с [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) , и [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) методы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## <a name="enumeration-values"></a>Значения перечисления  
  
|||  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|Скрипт был только что создан, но есть еще не был инициализирован с помощью `IPersist*` интерфейс и [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Скрипт был инициализирован, но не выполняется (подключение к другим объектам или получение событий) или выполнения любого кода. Код может запрашиваться для выполнения путем вызова [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md) метод.|  
|SCRIPTSTATE_STARTED|Скрипт можно выполнить код, но не еще прием событий объекты, добавленные с [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) метод.|  
|SCRIPTSTATE_CONNECTED|Скрипт загружен и подключен для получения событий.|  
|SCRIPTSTATE_DISCONNECTED|Скрипт загружается и находится в состоянии во время выполнения, но временно отключен от получения событий.|  
|SCRIPTSTATE_CLOSED|Скрипт был закрыт. Обработчик скриптов больше не работает и возвращает ошибки для большинства методов.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и коды ошибок активных скриптов](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)