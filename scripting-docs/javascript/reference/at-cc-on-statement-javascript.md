---
title: "Оператор @cc_on (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "@cc_on_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "@cc_on - оператор"
  - "@if - оператор"
  - "@set - оператор"
  - "условная компиляция, активация"
ms.assetid: fdeda7ee-b9f4-4e52-8aa2-21c90c02a332
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Оператор @cc_on (JavaScript)
Активирует поддержку условной компиляции внутри комментариев скрипта.  
  
> [!WARNING]
>  Условная компиляция не поддерживается стандартном режиме Internet Explorer 11 и в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  Она поддерживается в стандартном режиме Internet Explorer 10 и более ранних версий.  
  
## Синтаксис  
  
```  
@cc_on   
```  
  
## Заметки  
 Оператор `@cc_on` активирует условную компиляцию внутри комментариев скрипта.  
  
 Однако в скриптах, предназначенных для страниц ASP или ASP.NET и программ командной строки, переменные условной компиляции используются не так часто, поскольку характеристики компиляторов можно определить другими методами.  
  
 При создании скрипта для веб\-страницы следует всегда помещать код условной компиляции в комментарии.  Таким образом узлы, не поддерживающие условную компиляцию, смогут его пропустить.  
  
 Настоятельно рекомендуется помещать оператор `@cc_on` в комментарий, чтобы синтаксис скрипта был допустимым для браузеров, не поддерживающих условную компиляцию.  
  
 Условную компиляцию можно также включить с помощью оператора `@if` или `@set`, помещенного за пределами комментария.  
  
## Пример  
 В следующем примере показано использование оператора `@cc_on`.  
  
```javascript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on the 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on the 16-bit version of Windows.");  
    @else  
        document.write("Running on a different operating system.");  
    @end  
@*/  
```  
  
## Требования  
 Поддерживается во всех версиях Internet Explorer, но не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## См. также  
 [Условная компиляция](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Переменные условной компиляции](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [Оператор @if](../../javascript/reference/at-if-statement-javascript.md)   
 [Оператор @set](../../javascript/reference/at-set-statement-javascript.md)