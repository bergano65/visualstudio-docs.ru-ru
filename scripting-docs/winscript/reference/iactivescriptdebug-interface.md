---
title: "Интерфейс IActiveScriptDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptDebug — интерфейс"
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IActiveScriptDebug
Реализованный командами сценария, поддерживающие отладку.  Обычно объект, средства интерфейс `IActiveScriptDebug` также реализуют интерфейс `IActiveScript`.  В этом случае вызовите метод `IActiveScript::QueryInterface` чтобы получить интерфейс `IActiveScriptDebug`.  
  
 Интерфейс `IActiveScriptDebug` предоставляет середины для:  
  
-   Промежуточные узлы для принятия более управление документами.  
  
-   Процесс отладки диспетчер, чтобы синхронизировать отладка нескольких обработчиков скриптов.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IActiveScriptDebug` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|Возвращает атрибуты текста для произвольного фрагмента текста скрипта.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|Возвращает атрибуты текста для произвольного скрипта.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|Делегаты в `IDebugDocumentContext::EnumCodeContexts`.|