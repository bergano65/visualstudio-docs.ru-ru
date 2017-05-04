---
title: "IActiveScriptParse | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptParse — интерфейс"
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse
Если обработчик скриптов Windows позволяет сценарии кода начального текст, добавляемый к скрипту или разрешает текст выражения, которое вычисляется во время выполнения, он реализует интерфейс `IActiveScriptParse`.  Для интерпретированных языков скриптов, не имеющие независимую среды разработки, такими как VBScript, это обеспечивает альтернативный механизм \(за исключением `IPersist*`\), чтобы получить код скрипта в обработчик скриптов и вложить фрагменты скрипта на различные события объекта.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Инициализирует обработчика скриптов.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Добавляет сценарий кода к скрипту.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Анализирует заданную сценарий кода, при добавлении объявления в пространство имени и при оценке код подходит.|  
  
## См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)