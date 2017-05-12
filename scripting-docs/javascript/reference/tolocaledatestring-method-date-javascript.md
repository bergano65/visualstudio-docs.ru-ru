---
title: "Метод toLocaleDateString (Date) (JavaScript) | Microsoft Docs"
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
  - "toLocaleDateString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleDateString - метод"
ms.assetid: 0b83715c-8ced-4bd7-8940-a8007d002d10
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Метод toLocaleDateString (Date) (JavaScript)
Возвращает дату в виде строки, соответствующей текущему языковому стандарту хост\-среды или заданному языковому стандарту.  
  
## Синтаксис  
  
```  
  
dateObj.toLocaleDateString( [locales][, options])   
```  
  
#### Параметры  
 `dateObj`  
 Обязательное.  Объект `Date`.  
  
 `locales`  
 Необязательный параметр.  Массив строк языкового стандарта, которые содержат один или несколько тегов языка или языкового стандарта.  Если включить несколько строк языкового стандарта, нужно перечислить их в порядке убывания приоритета, чтобы первая запись была предпочитаемым языковым стандартом.  Если пропустить этот параметр, то используется языковой стандарт по умолчанию среды выполнения JavaScript.  
  
 `options`  
 Необязательный параметр.  Объект, содержащий одно или несколько свойств, определяющих параметры сравнения.  
  
## Заметки  
 Начиная с версии Internet Explorer 11, `toLocaleDateString` использует `Intl.DateTimeFormat` внутренне для форматирования даты, благодаря чему добавлена поддержка параметров `locales` и `options`.  Дополнительные сведения об этих параметрах см. в разделе [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Параметры `locales` и `options` поддерживаются не во всех версиях режимах документа и браузера.  Дополнительные сведения см. в разделе "Требования".  
  
 При использовании `toLocaleDateString` в режиме стандартного документа Internet Explorer 10 и более ранних режимах документов и режиме совместимости:  
  
-   он возвращает строковое значение, содержащее дату в текущем часовом поясе.  
  
-   Возвращаемая Дата представляется в формате, используемом по умолчанию в текущем языковом стандарте хост\-среды.  
  
 Если параметр `locales` опущен, возвращаемое значение этого метода невозможно использовать в скриптах, поскольку оно изменяется в зависимости от компьютера.  В этом сценарии, используйте метод только для форматирования отображаемого текста, но никогда как часть вычисления.  
  
## Пример  
 В следующем примере показано, как использовать метод `toLocaleDateString` с конкретным языковым стандартом и параметрами сравнения.  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleDateString("ar-SA", options));  
document.write(date.toLocaleDateString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎   
// ‎2013‎年‎2‎月‎1‎日‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 Параметры `locales` и `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## См. также  
 [Метод toDateString \(Date\)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [Метод toLocaleTimeString \(Date\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)