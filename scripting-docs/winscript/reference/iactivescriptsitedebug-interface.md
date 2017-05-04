---
title: "Интерфейс IActiveScriptSiteDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteDebug — интерфейс"
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IActiveScriptSiteDebug
Промежуточные узлы реализуют интерфейс `IActiveScriptSiteDebug` для управления документами и участвовать в отладке.  Объект `IActiveScriptSite` обычно обеспечивает реализацию интерфейса `IActiveScriptSiteDebug`.  Если это сделано, вызовите метод `IActiveScriptSite::QueryInterface` чтобы получить интерфейс `IActiveScriptSiteDebug`.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IActiveScriptSiteDebug` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Используемый обработчиком языка, чтобы делегировать `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Возвращает объект приложения отладки, связанный с этим сайтом скрипта.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Получает узел приложения, под которым должны быть добавитьы документы скрипта.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Обеспечивает промежуточный узел, чтобы указать способ обработки ошибок во время выполнения.|