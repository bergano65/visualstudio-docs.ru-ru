---
title: "Интерфейс IActiveScriptErrorDebug | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug interface
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ff2dda33c1e406f87a157173c41015acf96e62a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripterrordebug-interface"></a>Интерфейс IActiveScriptErrorDebug
Предоставляет сведения о контексте документа для ошибки времени компиляции и исключения во время выполнения. `IActiveScriptError::QueryInterface` Поддерживает метод `IActiveScriptErrorDebug` интерфейса.  
  
 Помимо методов, наследуемых от `IActiveScriptError`, `IActiveScriptErrorDebug` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Предоставляет контекст документа для этой ошибки.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Предоставляет кадр стека, которая действует для ошибок времени выполнения.|