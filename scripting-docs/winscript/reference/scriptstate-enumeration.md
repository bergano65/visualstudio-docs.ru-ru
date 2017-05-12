---
title: "Перечисление SCRIPTSTATE | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTSTATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTSTATE — перечисление"
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Перечисление SCRIPTSTATE
Указывает состояние обработчика скриптов.  Это перечисление используется методами [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md), [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) и [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md).  
  
## Синтаксис  
  
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
  
## Значения перечисления  
  
|||  
|-|-|  
|SCRIPTSTATE\_UNINITIALIZED|Скрипт просто был создания, но еще не был инициализирован с помощью интерфейса и [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)`IPersist*`.|  
|SCRIPTSTATE\_INITIALIZED|Был инициализирован, но не запускает \(подключение к другим объектам или тонуть события\) или не выполняет скрипт код.  Код можно запросить для выполнения путем вызова метода [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md).|  
|SCRIPTSTATE\_STARTED|Скрипт может выполнять код, но еще не тонет события объектов, добавленные методом [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md).|  
|SCRIPTSTATE\_CONNECTED|Скрипт загружен и подключения для тонуть событий.|  
|SCRIPTSTATE\_DISCONNECTED|Скрипт загружен и имеет состояние среды выполнения выполнения, но временное отключение от тонуть событий.|  
|SCRIPTSTATE\_CLOSED|Скрипт был закрыть.  Обработчик скриптов больше не работает и не возвращает ошибок для большинства методов.|  
  
## См. также  
 [Константы, перечисления и коды ошибок активных скриптов](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)