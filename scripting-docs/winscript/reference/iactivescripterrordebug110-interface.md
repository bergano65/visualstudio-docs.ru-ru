---
title: "IActiveScriptErrorDebug110 — интерфейс | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug110 — интерфейс"
ms.assetid: 5c1a4993-4cad-4ccf-89c2-53abfddfe1f2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptErrorDebug110 — интерфейс
Добавляет функциональные возможности в [Интерфейс IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md).  Этот интерфейс реализуется обработчиком JavaScript, чтобы определить, почему произошло событие BREAKREASON\_ERROR.  
  
> [!IMPORTANT]
>  Этот интерфейс реализуется в PDM v11.0 и более поздней версии.  Обнаружено в activdbg100.h.  
  
## Методы  
 Интерфейс `IActiveScriptErrorDebug110` предоставляет следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)|Возвращает вид исключения для созданного исключения.|