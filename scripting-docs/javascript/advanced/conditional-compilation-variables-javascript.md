---
title: Переменные условной компиляции (JavaScript) | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, variables
ms.assetid: d6f9827d-c558-412c-8e68-de04c19c3d9d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 900a44dab0ad418cd2899af6423f78016c90fe2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569124"
---
# <a name="conditional-compilation-variables-javascript"></a>Переменные условной компиляции (JavaScript)
Ниже приведен список предопределенных переменных, доступных для условной компиляции. Если переменная не равна **true**, она не определена и при доступе ведет себя как `NaN`.  
  
> [!WARNING]
>  Условная компиляция поддерживается во всех версиях Internet Explorer, предшествующих Internet Explorer 11. В стандартном режиме Internet Explorer 11 и более поздних версий и в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] условная компиляция не поддерживается.  
  
## <a name="variables"></a>Переменные  
  
|Переменная|Описание|  
|--------------|-----------------|  
|@_win32|Значение true при выполнении в системе Win32.|  
|@_win16|Значение true при выполнении в системе в системе Win16.|  
|@_mac|Значение true при выполнении в системе Apple Macintosh.|  
|@_alpha|Значение true при выполнении на процессоре DEC Alpha.|  
|@_x86|Значение true при выполнении на процессоре Intel.|  
|@_mc680x0|Значение true при выполнении на процессоре Motorola 680x0.|  
|@_PowerPC|Значение true при выполнении на процессоре Motorola PowerPC.|  
|@_jscript|Всегда имеет значение true.|  
|@_jscript_build|Содержит номер сборки обработчика скриптов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].|  
|@_jscript_version|Содержит номер версии [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] в формате "основная.дополнительная".|