---
title: "Интерфейс IActiveScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug — интерфейс"
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IActiveScriptErrorDebug
Предоставляет сведения о контексте документа для ошибок времени компиляции и исключений среды выполнения.  Метод `IActiveScriptError::QueryInterface` поддерживает интерфейс `IActiveScriptErrorDebug`.  
  
 В дополнение к методам, наследуемым от интерфейса `IActiveScriptError`, интерфейс `IActiveScriptErrorDebug` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Предоставляет контекст рисования для этой ошибки.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Предоставляет кадр стека, действующей для продолжающих ошибок.|