---
title: "Оператор @set (JavaScript) | Microsoft Docs"
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
  - "@set_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "@set - оператор"
  - "условная компиляция, переменные"
ms.assetid: 36f15926-3e69-422d-82a2-d186dc088203
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Оператор @set (JavaScript)
Создает переменные, используемые вместе с операторами условной компиляции.  
  
> [!WARNING]
>  Условная компиляция не поддерживается стандартном режиме Internet Explorer 11 и в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  Она поддерживается в стандартном режиме Internet Explorer 10 и более ранних версий.  
  
## Синтаксис  
  
```  
  
@set @varname = term   
```  
  
## Параметры  
 *varname*  
 Обязательный.  Допустимое имя переменной [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Должно всегда предваряться знаком "@".  
  
 `term`  
 Обязательный.  Ноль или более унарных операторов, за которыми следует константа, переменная условной компиляции или выражение в скобках.  
  
## Заметки  
 В коде условной компиляции поддерживаются числовые и логические переменные.  Строки не поддерживаются.  Переменные, созданные с помощью оператора `@set`, обычно используются в операторах условной компиляции, но могут применяться и в любом другом коде [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 Ниже приведены примеры объявлений переменных.  
  
```javascript  
  
        @set @myvar1 = 12  
  
@set @myvar2 = (@myvar1 * 20)  
  
@set @myvar3 = @_jscript_version  
```  
  
 Следующие операторы можно использовать в выражениях, заключенных в скобки.  
  
-   `!  ~`  
  
-   `* / %`  
  
-   `+ -`  
  
-   `<< >> >>>`  
  
-   `< <= > >=`  
  
-   `== != === !==`  
  
-   `& ^ |`  
  
-   `&& | |`  
  
 Если переменная используется до своего определения, ее значение равно `NaN`.  Проверку на наличие значения `NaN` можно выполнить с помощью оператора `@if`:  
  
```javascript  
@if (@newVar != @newVar)  
   ...  
```  
  
 Этот метод дает правильный результат, поскольку `NaN` является единственным значением, которое не равно самому себе.  
  
## Требования  
 Поддерживается во всех версиях Internet Explorer, но не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## См. также  
 [Условная компиляция](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Переменные условной компиляции](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [Оператор @cc\_on](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [Оператор @if](../../javascript/reference/at-if-statement-javascript.md)