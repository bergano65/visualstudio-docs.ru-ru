---
title: "Переменные условной компиляции (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "условная компиляция, переменные"
ms.assetid: d6f9827d-c558-412c-8e68-de04c19c3d9d
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Переменные условной компиляции (JavaScript)
Ниже приведен список предопределенных переменных, доступных для условной компиляции.  Если переменная не равна **true**, она не определена и при доступе ведет себя как `NaN`.  
  
> [!WARNING]
>  Условная компиляция поддерживается во всех версиях Internet Explorer, предшествующих Internet Explorer 11.  В стандартном режиме Internet Explorer 11 и более поздних версий и в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] условная компиляция не поддерживается.  
  
## Переменные  
  
|Переменная|Описание|  
|----------------|--------------|  
|@\_win32|Значение true при выполнении в системе Win32.|  
|@\_win16|Значение true при выполнении в системе в системе Win16.|  
|@\_mac|Значение true при выполнении в системе Apple Macintosh.|  
|@\_alpha|Значение true при выполнении на процессоре DEC Alpha.|  
|@\_x86|Значение true при выполнении на процессоре Intel.|  
|@\_mc680x0|Значение true при выполнении на процессоре Motorola 680x0.|  
|@\_PowerPC|Значение true при выполнении на процессоре Motorola PowerPC.|  
|@\_jscript|Всегда имеет значение true.|  
|@\_jscript\_build|Содержит номер сборки обработчика скриптов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].|  
|@\_jscript\_version|Содержит номер версии [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] в формате "основная.дополнительная".|