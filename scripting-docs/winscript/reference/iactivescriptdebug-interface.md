---
title: "Интерфейс IActiveScriptDebug | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptDebug interface
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1e1d0c1cf51c63f1bb3fcd90ae72520da907e50
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebug-interface"></a>Интерфейс IActiveScriptDebug
Реализовать обработчики скриптов, поддерживающие отладку. Как правило, объект, реализующий интерфейс `IActiveScriptDebug` также интерфейс реализует `IActiveScript` интерфейса. Если это так, вызовите `IActiveScript::QueryInterface` метод, чтобы получить `IActiveScriptDebug` интерфейса.  
  
 `IActiveScriptDebug` Интерфейс предоставляет средства для:  
  
-   Промежуточные узлы берет на себя управление документами.  
  
-   Диспетчер процессов отладки для синхронизации, отладка нескольких обработчиков сценария.  
  
 Помимо методов, наследуемых от `IUnknown`, `IActiveScriptDebug` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|Возвращает атрибуты текста для произвольного блок текста сценария.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|Возвращает атрибуты текста для произвольного сценариев.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|Делегирует `IDebugDocumentContext::EnumCodeContexts`.|