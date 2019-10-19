---
title: Перечисление СКРИПТСТАТЕ | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 10dd6366e2d0783ec2e9d6bdadc001e9f999901e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575684"
---
# <a name="scriptstate-enumeration"></a>Перечисление SCRIPTSTATE
Указывает состояние обработчика скриптов. Это перечисление используется методами [IActiveScript:: жетскриптстате](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript:: SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) и [IActiveScriptSite:: онстатечанже](../../winscript/reference/iactivescriptsite-onstatechange.md) .  
  
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
|SCRIPTSTATE_UNINITIALIZED|Сценарий только что был создан, но еще не был инициализирован с помощью интерфейса `IPersist*` и [IActiveScript:: сетскриптсите](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Сценарий инициализирован, но не выполняется (подключение к другим объектам или события приемника) или выполнение кода. Код можно запросить для выполнения, вызвав метод [IActiveScriptParse::P арсескрипттекст](../../winscript/reference/iactivescriptparse-parsescripttext.md) .|  
|SCRIPTSTATE_STARTED|Скрипт может выполнять код, но еще не перемещает события объектов, добавленных методом [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|SCRIPTSTATE_CONNECTED|Сценарий загружен и подключен к событиям приемника.|  
|SCRIPTSTATE_DISCONNECTED|Сценарий загружен и имеет состояние выполнения во время выполнения, но временно отключен от приемника событий.|  
|SCRIPTSTATE_CLOSED|Скрипт был закрыт. Обработчик скриптов больше не работает и возвращает ошибки для большинства методов.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и коды ошибок активных скриптов](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)