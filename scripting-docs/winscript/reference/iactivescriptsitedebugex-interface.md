---
title: "IActiveScriptSiteDebugEx — интерфейс | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteDebugEx — интерфейс"
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebugEx — интерфейс
Реализуйте этот интерфейс вместе с интерфейсом `IActiveScriptSiteDebug` при написании основное приложение, которому требуется получить уведомление ошибки во время выполнения приложения и вложить в приложение для отладки.  Диспетчер процесса отладки предоставляет уведомление с помощью jit\-компилятора `IActiveScriptDebug` если отладчик скриптов найти на компьютере.  Если jit\-отладка отладчик скриптов не найден, то PDM предоставляет уведомление по `IActiveScriptDebugEx`.  
  
 Чтобы получать уведомления об ошибках во время выполнения, основное приложение должно обрабатывать [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/ru-ru/cf7639f9-a699-4571-9f3a-82ef52c0b5f4).  На основе действию пользователя, после этого можно принять решение, следует ли отладчик вложен внутренние и извлечение или вернуть запуск отладчика в параметре OnScriptErrorDebug `pfEnterDebugger`.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Уведомляет основное приложение о ошибках во время выполнения скрипта, если диспетчер процесса отладки не находит внешнее только в отладчике Time.|