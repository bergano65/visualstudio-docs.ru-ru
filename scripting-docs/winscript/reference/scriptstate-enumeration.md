---
title: Перечисление SCRIPTSTATE | Документы Microsoft
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
ms.openlocfilehash: 35e062a9c2f3076144063ffb77895c8a03ecc4ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734284"
---
# <a name="scriptstate-enumeration"></a>Перечисление SCRIPTSTATE
Задает состояние обработчика сценариев. Это перечисление используется методом [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) , и [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) методы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
|SCRIPTSTATE_UNINITIALIZED|Сценарий уже создан, но еще не была инициализирована с использованием `IPersist*` интерфейс и [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Скрипт был инициализирован, но не выполняется (подключение к другим объектам или прием событий) или выполнения любого кода. Код можно запрашивать выполнения путем вызова [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md) метод.|  
|SCRIPTSTATE_STARTED|Сценарий может выполняться код, но не еще прием событий для объектов, добавленных с [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) метод.|  
|SCRIPTSTATE_CONNECTED|Сценарий загружен и подключен для прием событий.|  
|SCRIPTSTATE_DISCONNECTED|Сценарий загружается и находится в состоянии во время выполнения, но временно отключен от прием событий.|  
|SCRIPTSTATE_CLOSED|Скрипт был закрыт. Обработчик скриптов больше не работает и возвращает ошибки для большинства методов.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и коды ошибок активных скриптов](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)