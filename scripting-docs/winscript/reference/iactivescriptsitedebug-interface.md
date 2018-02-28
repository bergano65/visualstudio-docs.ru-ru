---
title: "Интерфейс IActiveScriptSiteDebug | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9b36054deeceb0528fb7ea399cc41d8edbbb47e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug-interface"></a>Интерфейс IActiveScriptSiteDebug
Промежуточные узлы реализовать `IActiveScriptSiteDebug` интерфейс для управления документами и участвовать в отладке. `IActiveScriptSite` Объект обычно предоставляет реализацию `IActiveScriptSiteDebug` интерфейса. Если это сделано, вызовите `IActiveScriptSite::QueryInterface` метод, чтобы получить `IActiveScriptSiteDebug` интерфейса.  
  
 Помимо методов, наследуемых от `IUnknown`, `IActiveScriptSiteDebug` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Использовать обработчик языка для делегирования `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Возвращает объект отладки приложения, связанный с этим узлом скрипта.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Возвращает узел приложения, в какой скрипт документы должны быть добавлены.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Позволяет промежуточных узлов определить способ обработки ошибок во время выполнения.|