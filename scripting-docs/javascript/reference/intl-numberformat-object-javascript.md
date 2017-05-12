---
title: "Объект Intl.NumberFormat (JavaScript) | Microsoft Docs"
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
  - "NumberFormat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Объект Intl.NumberFormat (JavaScript)
Содержит форматирование чисел, соответствующее языковому стандарту.  
  
## Синтаксис  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### Параметры  
 `numberFormatObj`  
 Обязательное.  Имя переменной, к которой нужно присвоить объект `NumberFormat`.  
  
 `locales`  
 Необязательный параметр.  Массив строк языкового стандарта, которые содержат один или несколько тегов языка или языкового стандарта.  Если включить несколько строк языкового стандарта, нужно перечислить их в порядке убывания приоритета, чтобы первая запись была предпочитаемым языковым стандартом.  Если пропустить этот параметр, то используется языковой стандарт по умолчанию среды выполнения JavaScript.  Дополнительные сведения см. в разделе "Примечания".  
  
 `options`  
 Необязательный параметр.  Объект, содержащий одно или несколько свойств, определяющих параметры форматирования числа.  Дополнительные сведения см. в разделе "Заметки".  
  
## Заметки  
 Параметр `locales` должен соответствовать тегам языка или языкового стандарта [BCP 47](http://tools.ietf.org/html/rfc5646), таким как "en\-US" и "zh\-CN".  Тег может включать язык, регион, страну и вариант.  Примеры тегов языка, см. в разделе [Приложение А](http://tools.ietf.org/html/rfc5646#appendix-A) к BCP 47.  Для `NumberFormat` можно добавить подтег **\-u**, за которым добавить \-nu для определения расширения системы нумерации:  
  
 "*language*\-*region*\-u\-nu\-*numberingsystem*"  
  
 где *numberingsystem* может быть одним из следующих: arab, arabext, bali, beng, deva, fullwide, gujr, guru, hanidec, khmr, knda, laoo, latn, limb, mylm, mong, mymr, orya, tamldec, telu, thai, tibt.  
  
 Параметр `options` может включать следующие свойства:  
  
|Свойство|Описание|Возможные значения|Значение по умолчанию|  
|--------------|--------------|------------------------|---------------------------|  
|`localeMatcher`|Задает используемый алгоритм подбора языкового стандарта.|"lookup", "best fit"|"best fit"|  
|`style`|Задает стиль формата чисел.|"decimal", "percent", "currency"|"decimal"|  
|`currency`|Задает значение валюты ISO 4217 как алфавитный код.  Это значение требуется, если `style` задано как "валюта".|См. в разделе ISO [список кодов валют и фондов](http://www.currency-iso.org/en/home/tables/table-a1.html).|undefined|  
|`currencyDisplay`|Указывает, отображать ли валюту как алфавитный код валюты ISO 4217, как локализованный символ валюты или как локализованное имя валюты.  Это значение используется, только если свойство `style` имеет значение "currency".|"code", "symbol", "name"|"symbol"|  
|`useGrouping`|Указывает, должен ли использоваться разделитель группирования.|true, false|`true`.|  
|`minimumIntegerDigits`|Задает минимальное число цифр целой части для использования.|От 1 до 21.|21|  
|`minimumFractionDigits`|.  Задает минимальное число цифр дробной части для использования.|От 0 до 20.|0|  
|`maximumFractionDigits`|Задает максимальное число цифр дробной части для использования.|Это значение может меняться в диапазоне от `minimumFractionDigits` до 20.|20.|  
|`minimumSignificantDigits`|Задает минимальное число цифр дробной части для отображения.|Это значение может меняться в диапазоне от 1 до 21.|1|  
|`maximumSignificantDigits`|Задает максимальное число цифр дробной части для отображения.|Это значение может меняться в диапазоне от `minimumSignificantDigits` до 21.|21|  
  
## Свойства  
 В следующей таблице перечислены свойства объекта `NumberFormat`.  
  
|||  
|-|-|  
|Свойство|Описание|  
|[Конструктор](../../javascript/reference/constructor-property-intl-numberformat.md)|Указывает функцию, которая создает объект средства форматирования числа.|  
|[format](../../javascript/reference/format-property-intl-numberformat.md)|Возвращает функцию, которая форматирует число, используя настройки средства форматирования числа.|  
|[прототип](../../javascript/reference/prototype-property-intl-numberformat.md)|Возвращает ссылку на прототип для модуля форматирования числа.|  
  
## Методы  
 В следующей таблице перечислены методы объекта `NumberFormat`.  
  
|||  
|-|-|  
|Метод|Описание|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|Возвращает объект, содержащий свойства и значения объекта средства форматирования числа.|  
  
## Пример  
 В следующем примере создается объект `NumberFormat` для языкового стандарта en\-US с указанными параметрами форматирования.  
  
```javascript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
});  
  
if (console && console.log) {  
    console.log(nf.format(100)); // Returns ¥100.00  
}  
```  
  
## Пример  
 В следующих примерах показаны результаты использования нескольких различных языковых стандартов и параметров.  
  
```javascript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
if (console && console.log) {  
    console.log(new Intl.NumberFormat("en-US").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ja-JP").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ar-SA", options1).format(number));  
    // Returns ١٢,٣٤٥,٦٧٨,٩٠٠ %  
    console.log(new Intl.NumberFormat("hi-IN", options2).format(number));  
    // Returns ₹ 12,34,56,789.00  
}  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## См. также  
 [toLocaleString \(Number\)](../../javascript/reference/tolocalestring-number.md)   
 [Объект Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md)   
 [Объект Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)