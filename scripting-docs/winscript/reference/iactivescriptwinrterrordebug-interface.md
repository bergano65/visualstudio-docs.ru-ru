---
title: "IActiveScriptWinRTErrorDebug — интерфейс | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptWinRTErrorDebug — интерфейс"
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptWinRTErrorDebug — интерфейс
Реализуемый обработчиком JavaScript для предоставления дополнительных сведений об ошибках Windows из среды выполнения события [Перечисление BREAKREASON](../../winscript/reference/breakreason-enumeration.md).  Это можно сделать QueryInterface для получения из объекта [IActiveScriptError](../../winscript/reference/iactivescripterror.md).  
  
> [!IMPORTANT]
>  Этот интерфейс реализуется PDM v11.0 и большим.  Обнаружен в activdbg100.h.  
  
## Методы  
 Интерфейс `IActiveScriptWinRTErrorDebug` предоставляет следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Возвращает идентификатор безопасности возможности для ошибок среды выполнения Windows, если оно известно.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Возвращает строку среды выполнения ссылки ошибок Windows ограниченную, если оно известно.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Возвращает строку ошибки Windows ограничиванную средой выполнения, если оно известно.|