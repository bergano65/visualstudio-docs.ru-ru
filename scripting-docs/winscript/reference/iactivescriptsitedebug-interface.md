---
title: Интерфейс IActiveScriptSiteDebug | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cd8043648586ed3c614cbb137e51d992d7ae29b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992468"
---
# <a name="iactivescriptsitedebug-interface"></a>Интерфейс IActiveScriptSiteDebug
Реализовать промежуточных узлов `IActiveScriptSiteDebug` интерфейс для выполнения управления документами и участвовать в отладке. `IActiveScriptSite` Объект обычно содержит реализацию `IActiveScriptSiteDebug` интерфейс. Если это сделано, вызовите `IActiveScriptSite::QueryInterface` метод, чтобы получить `IActiveScriptSiteDebug` интерфейс.  
  
 Помимо методов, наследуемых от `IUnknown`, `IActiveScriptSiteDebug` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Используемый модуль языка делегировать `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Возвращает объект отладки приложения, связанные с этим сайтом скрипта.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Получает узел приложения, в области какой сценарий следует добавить документы.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Позволяет промежуточный узел определить способ обработки ошибок времени выполнения.|