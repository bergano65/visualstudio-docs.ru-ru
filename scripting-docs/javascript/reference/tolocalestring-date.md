---
title: "toLocaleString (Date) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# toLocaleString (Date)
Преобразует дату в строку, используя текущий или указанный языковой стандарт.  
  
## Синтаксис  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### Параметры  
 `dateObj`  
 Обязательное.  Преобразуемый объект `Date`.  
  
 `locales`  
 Необязательный параметр.  Массив строк языкового стандарта, которые содержат один или несколько тегов языка или языкового стандарта.  Если включить несколько строк языкового стандарта, нужно перечислить их в порядке убывания приоритета, чтобы первая запись была предпочитаемым языковым стандартом.  Если пропустить этот параметр, то используется языковой стандарт по умолчанию среды выполнения JavaScript.  
  
 `options`  
 Необязательный параметр.  Объект, содержащий одно или несколько свойств, определяющих параметры сравнения.  
  
## Заметки  
 Начиная с версии Internet Explorer 11, `toLocaleString` использует `Intl.DateTimeFormat` внутренне для сравнения, благодаря чему добавлена поддержка параметров `locales` и `options`.  Дополнительные сведения об этих параметрах см. в разделе [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Параметры `locales` и `options` поддерживаются не во всех версиях режимах документа и браузера.  Дополнительные сведения см. в разделе "Требования".  
  
 При использовании `toLocaleString` в режиме стандартного документа Internet Explorer 10 и более ранних режимах документов и режиме совместимости:  
  
-   Возвращает объект `String`, который содержит дату, записанную в длинном формате, принятом по умолчанию в текущем языковом стандарте.  
  
-   Даты в диапазоне от 1601 до 1999 года нашей эры форматируются в соответствии с региональными параметрами, установленными на панели управления пользователя.  
  
> [!NOTE]
>  Если опущен параметр `locales`, используйте `toLocaleString` только для отображения результатов пользователю; никогда не используйте его для вычисления значения в скрипте, поскольку возвращаемый результат связан с текущим компьютером.  
  
## Пример  
 В следующем примере показано, как использовать метод `toLocaleString`.  
  
```javascript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## Пример  
 В следующем примере показано, как использовать метод `toLocaleString` с конкретным языковым стандартом и параметрами сравнения.  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleString("en-US"));  
document.write(date.toLocaleString("ja-JP"));  
document.write(date.toLocaleString("ar-SA", options));  
document.write(date.toLocaleString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎ ‎6‎:‎00‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎ ‎6‎:‎00‎:‎00  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 Параметры `locales` и `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## См. также  
 [Метод toLocaleDateString \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)