---
title: Интерфейс IActiveScriptSiteDebug32 | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: a752851aa6afd903747dc58fed79d2bc5b27e3e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725124"
---
# <a name="iactivescriptsitedebug32-interface"></a>Интерфейс IActiveScriptSiteDebug32
Промежуточные узлы реализовать `IActiveScriptSiteDebug32` интерфейс для управления документами и участвовать в отладке. `IActiveScriptSite` Объект обычно предоставляет реализацию `IActiveScriptSiteDebug32` интерфейса. Если это сделано, вызовите `IActiveScriptSite::QueryInterface` метод, чтобы получить `IActiveScriptSiteDebug32` интерфейса.  
  
 Помимо методов, наследуемых от `IUnknown`, `IActiveScriptSiteDebug32` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Возвращает объект отладки приложения, связанный с этим узлом скрипта.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Использовать обработчик языка для делегирования `IDebugCodeContext::GetSourceContext`.|