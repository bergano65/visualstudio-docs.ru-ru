---
title: "toLocaleString (Number) | Microsoft Docs"
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
ms.assetid: 42c05252-13c1-4943-b1a4-b33285aeab3e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# toLocaleString (Number)
Преобразует число в в строку, используя текущий или указанный языковой стандарт.  
  
## Синтаксис  
  
```  
  
numberObj.toLocaleString([locales][, options])   
```  
  
#### Параметры  
 `numberObj`  
 Обязательное.  Преобразуемый объект `Number`.  
  
 `locales`  
 Необязательный параметр.  Массив строк языкового стандарта, которые содержат один или несколько тегов языка или языкового стандарта.  Если включить несколько строк языкового стандарта, нужно перечислить их в порядке убывания приоритета, чтобы первая запись была предпочитаемым языковым стандартом.  Если пропустить этот параметр, то используется языковой стандарт по умолчанию среды выполнения JavaScript.  
  
 `options`  
 Необязательный параметр.  Объект, содержащий одно или несколько свойств, определяющих параметры сравнения.  
  
## Заметки  
 Начиная с версии Internet Explorer 11, `toLocaleString` использует `Intl.NumberFormat` внутренне для сравнения, благодаря чему добавлена поддержка параметров `locales` и `options`.  Дополнительные сведения об этих параметрах см. в разделе [Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Параметры `locales` и `options` поддерживаются не во всех версиях режимах документа и браузера.  Дополнительные сведения см. в разделе "Требования".  
  
> [!NOTE]
>  Если опущен параметр `locales`, используйте `toLocaleString` только для отображения результатов пользователю; никогда не используйте его для вычисления значения в скрипте, поскольку возвращаемый результат связан с текущим компьютером \(метод возвращает текущий языковой стандарт\).  
  
## Пример  
 В следующем примере показано, как использовать метод `toLocaleString` без параметров.  
  
```javascript  
var n, s;  
n = new Number(100);  
s = "Current locale value is: ";  
s += n.toLocaleString();                 
document.write(s);  
  
// Output:  
// The value 100 as represented by the current locale.  
```  
  
## Пример  
 В следующем примере показано, как использовать метод `toLocaleString` с конкретным языковым стандартом и параметрами сравнения.  
  
```javascript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
document.write(number.toLocaleString("en-US"));  
// 123,456,789  
document.write(number.toLocaleString("ja-JP"));  
// 123,456,789  
document.write(number.toLocaleString("ar-SA", options1));  
// ١٢,٣٤٥,٦٧٨,٩٠٠ %  
document.write(number.toLocaleString("hi-IN", options2));  
// ₹ 12,34,56,789.00  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 Параметры `locales` и `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## См. также  
 [Метод toLocaleDateString \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)