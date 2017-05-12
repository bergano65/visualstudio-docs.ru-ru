---
title: "Метод localeCompare (String) (JavaScript) | Microsoft Docs"
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
  - "localeCompare"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "localeCompare - метод"
ms.assetid: 66914079-12dd-4393-a84c-c05f58231c36
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Метод localeCompare (String) (JavaScript)
Определяет, являются ли две строки эквивалентными в текущем языковом стандарте.  
  
## Синтаксис  
  
```  
  
stringVar.localeCompare(stringExp[, locales][, options])   
```  
  
## Параметры  
 `stringVar`  
 Обязательное.  Первая сравниваемая строка.  
  
 `stringExp`  
 Обязательное.  Вторая сравниваемая строка.  
  
 `locales`  
 Необязательный параметр.  Массив строк языкового стандарта, которые содержат один или несколько тегов языка или языкового стандарта.  Если включить несколько строк языкового стандарта, нужно перечислить их в порядке убывания приоритета, чтобы первая запись была предпочитаемым языковым стандартом.  Если пропустить этот параметр, то используется языковой стандарт по умолчанию среды выполнения JavaScript.  Этот параметр должен соответствовать стандартам [BCP 47](http://tools.ietf.org/html/rfc5646); дополнительные сведения см. в описании [объекта Int.Collator](../../javascript/reference/intl-collator-object-javascript.md).  
  
 `options`  
 Необязательный параметр.  Объект, содержащий одно или несколько свойств, задающих параметры сравнения. Дополнительные сведения см. в разделе [Объект Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md).  
  
## Заметки  
 Для строк сравнения можно задавать либо объекты `String`, либо строковые литералы.  
  
 Начиная с версии Internet Explorer 11, `localeCompare` использует объект `Intl.Collator` внутренне для сравнения, благодаря чему добавлена поддержка параметров `locales` и `options`.  Дополнительные сведения об этих параметрах см. в разделах [Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) и [Intl.Collator.compare](../../javascript/reference/compare-property-intl-collator.md).  
  
> [!IMPORTANT]
>  Параметры `locales` и `options` поддерживаются не во всех версиях режимах документа и браузера.  Дополнительные сведения см. в разделе "Требования".  
  
 Метод `localeCompare` осуществляет сравнение \(с учетом языкового стандарта\) `stringVar` и `stringExp` и возвращает один из следующих результатов в зависимости от порядка сортировки в языке системы по умолчанию.  
  
-   \-1, если `stringVar` сортируется перед `stringExp`.  
  
-   \+1, если `stringVar` при сортировке размещается после `stringExp`.  
  
-   0 \(нуль\), если две строки эквивалентны.  
  
## Пример  
 Следующий код показывает, как использовать функцию `localeCompare`.  
  
```javascript  
var str1 = "def";  
var str2 = "abc"  
  
document.write(str1.localeCompare(str2) + "<br/>");  
  
// Output: 1  
var str3 = "ghi";  
  
document.write(str1.localeCompare(str3)+ "<br/>");  
  
// Output: -1  
var str4 = "def";  
  
document.write(str1.localeCompare(str4));  
  
// Output: 0  
```  
  
## Пример  
 В следующем примере кода показано, как использовать `localeCompare` с языковым стандартом "Немецкий \(Германия\)".  
  
```javascript  
var str1 = "a";  
var str2 = "b";  
  
document.write(str1.localeCompare(str2, "de-DE"));  
  
// Output  
// - 1  
```  
  
## Пример  
 В следующем примере показано использование `localeCompare` с языковым стандартом "Немецкий \(Германия\)" и расширением для данного языкового стандарта, которое определяет порядок сортировки немецких телефонных справочников.  В этом примере показаны различия, связанные с языковым стандартом.  
  
```javascript  
var arr = ["ä", "ad", "af", "a"];  
  
document.write(arr[0].localeCompare(arr[1], "de-DE-u-co-phonebk"));  // Returns 1  
document.write (arr[0].localeCompare(arr[2], "de-DE-u-co-phonebk"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE-u-co-phonebk"));  // Returns 1  
  
document.write (arr[0].localeCompare(arr[1], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[2], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE"));  // Returns 1  
  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Параметры `locales` и `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## См. также  
 [Метод toLocaleString \(Object\)](../../javascript/reference/tolocalestring-method-object-javascript.md)