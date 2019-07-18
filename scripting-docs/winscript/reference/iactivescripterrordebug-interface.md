---
title: Интерфейс IActiveScriptErrorDebug | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug interface
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 936770859d3bdfe81c84245d32ae63346b142a01
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009536"
---
# <a name="iactivescripterrordebug-interface"></a>Интерфейс IActiveScriptErrorDebug
Предоставляет сведения о контексте документа для ошибки времени компиляции и исключения во время выполнения. `IActiveScriptError::QueryInterface` Поддерживает метод `IActiveScriptErrorDebug` интерфейс.  
  
 Помимо методов, наследуемых от `IActiveScriptError`, `IActiveScriptErrorDebug` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Предоставляет контекст документа, для этой ошибки.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Предоставляет кадр стека, который распространяется на ошибки времени выполнения.|