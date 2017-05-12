---
title: "Оператор @if (JavaScript) | Microsoft Docs"
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
  - "@if_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "@if - оператор"
  - "условные операторы, if"
  - "elif - оператор"
  - "else - оператор"
  - "if - оператор, @if"
ms.assetid: ff11b29d-c06a-4276-b11d-db73e2da98ac
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Оператор @if (JavaScript)
Выполняет ту или иную группу операторов в зависимости от значения выражения.  
  
> [!WARNING]
>  Условная компиляция не поддерживается стандартном режиме Internet Explorer 11 и в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  Она поддерживается в стандартном режиме Internet Explorer 10 и более ранних версий.  
  
## Синтаксис  
  
```  
  
      @if (  
   condition1  
)  
   text1  
[@elif (  
   condition2  
)  
   text2]  
[@else  
   text3]  
@end   
```  
  
## Параметры  
 *condition1, condition2*  
 Необязательный.  Выражение, которое можно привести к логическому выражению.  
  
 `text1`  
 Необязательный.  Текст для синтаксического анализа, если `condition1` равно **true**.  
  
 `text2`  
 Необязательный.  Текст для синтаксического анализа, если `condition1` равно **false** и `condition2` равно **true**.  
  
 `text3`  
 Необязательный.  Текст для синтаксического анализа, если `condition1` и `condition2` равны **false**.  
  
## Заметки  
 При написании оператора `@if` нет необходимости размещать каждое предложение на отдельной строке.  Можно использовать несколько предложений **@elif**.  Но все предложения **@elif** должны быть перед предложением **@else**.  
  
 Оператор `@if` обычно используется, чтобы определить, какой текст из нескольких вариантов следует вывести.  
  
 В скриптах, написанных для страниц ASP и ASP.NET, а также в программах командной строки переменные условной компиляции обычно не используются.  Это связано с тем, что возможности компиляторов можно определить другими методами.  
  
 При создании скрипта для веб\-страницы следует всегда помещать код условной компиляции в комментарии.  Таким образом узлы, не поддерживающие условную компиляцию, смогут его пропустить.  
  
## Пример  
 В следующем примере показано использование оператора **@if...@elif…@else...@end**.  
  
```javascript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on a 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on a 16-bit version of Windows.");  
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
 [Оператор @cc\_on](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [Оператор @set](../../javascript/reference/at-set-statement-javascript.md)