---
title: "IActiveScriptParseProcedure | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptParseProcedure — интерфейс"
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParseProcedure
Если обработчик скриптов Windows позволяет текст исходного кода для процедур, добавляемый к скрипту, он реализует интерфейс `IActiveScriptParseProcedure`.  Для интерпретированных языков скриптов, не имеющие независимую среды разработки, такими как VBScript, это обеспечивает альтернативный механизм \(за исключением `IActiveScriptParse` или `IPersist`\*\) чтобы добавить процедуры сценария к пространству имен.  
  
## Методы в порядке таблицы Vtable  
  
|||  
|-|-|  
|Метод|Описание|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Анализирует заданную процедура кода и добавляет процедура к пространству имен.|  
  
## См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)