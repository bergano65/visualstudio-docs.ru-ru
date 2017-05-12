---
title: "Объект Intl.DateTimeFormat (JavaScript) | Microsoft Docs"
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
  - "DateTimeFormat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: cc555ac2-f31c-4239-a612-b84c08e3a37f
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Объект Intl.DateTimeFormat (JavaScript)
Обеспечивает форматирование даты и времени, соответствующее языковому стандарту.  
  
## Синтаксис  
  
```  
dateTimeFormatObj = new Intl.DateTimeFormat([locales][, options])  
```  
  
#### Параметры  
 `dateTimeFormatObj`  
 Обязательный.  Имя переменной, которой нужно присвоить объект `DateTimeFormat`.  
  
 `locales`  
 Необязательный.  Массив строк языкового стандарта, которые содержат один или несколько тегов языка или языкового стандарта.  При включении нескольких строк языкового стандарта их следует перечислять в порядке убывания приоритета, чтобы первая запись была предпочитаемым языковым стандартом.  Если этот параметр опущен, используется языковой стандарт по умолчанию среды выполнения JavaScript.  Дополнительные сведения см. в разделе "Примечания".  
  
 `options`  
 Необязательный.  Объект, содержащий одно или несколько свойств, определяющих параметры форматирования даты и времени.  Подробные сведения см. в разделе "Заметки".  
  
## Заметки  
 Параметр `locales` должен соответствовать тегам языка или языкового стандарта [BCP 47](http://tools.ietf.org/html/rfc5646), например "en\-US" и "zh\-CN".  Тег может включать язык, регион, страну и вариант.  Примеры тегов языка см. в разделе [Приложение А](http://tools.ietf.org/html/rfc5646#appendix-A) BCP 47.  Для `DateTimeFormat` в строке языкового стандарта можно добавить подтег **\-u**, чтобы включить одно или оба из следующих расширений Юникода:  
  
-   \-nu для задания расширения системы нумерации: *language*\-*region*\-u\-nu\-*numberingsystem*  
  
     где *numberingsystem* может иметь одно из следующих значений: arab, arabext, bali, beng, deva, fullwide, gujr, guru, hanidec, khmr, knda, laoo, latn, limb, mylm, mong, mymr, orya, tamldec, telu, thai, tibt.  
  
-   \-ca для задания календаря: *language*\-*region*\-u\-ca\-*calendar*  
  
     где *calendar* может иметь одно из следующих значений: buddhist, chinese, gregory, islamic, islamicc, japanese.  
  
 Параметр `options` может содержать указанные ниже свойства.  
  
|Свойство|Описание|Возможные значения|Значение по умолчанию|  
|--------------|--------------|------------------------|---------------------------|  
|`localeMatcher`|Задает используемый алгоритм подбора языкового стандарта.|"lookup","best fit"|"best fit"|  
|`formatMatcher`|Задает используемый алгоритм подбора формата.|"basic", "best fit"|"best fit"|  
|`hour12`|Указывает, использовать ли для часов 12\-часовой формат.|`true` \(для 12\-часового формата\), `false` \(для 24\-часового формата\)||  
|`timeZone`|Задает часовой пояс.  Как минимум, всегда поддерживается "UTC".|Значение часового пояса, например "UTC".|"UTC"|  
|`weekday`|Задает форматирование дня недели.|"narrow", "short", "long"|Не определено|  
|`era`|Задает форматирование эры.|"narrow", "short", "long"|Не определено|  
|`year`|Задает форматирование года.|"2\-digit", "numeric"|Не определено или "numeric"|  
|`month`|Задает форматирование месяца.|"2\-digit", "numeric", "narrow", "short", "long"|Не определено или "numeric"|  
|`day`|Задает форматирование дня.|"2\-digit", "numeric"|Не определено или "numeric"|  
|`hour`|Задает форматирование часов.|"2\-digit", "numeric"|Не определено|  
|`minute`|Задает форматирование минут.|"2\-digit", "numeric"|Не определено|  
|`second`|Задает форматирование секунд.|"2\-digit", "numeric"|Не определено|  
|`timeZoneName`|Задает форматирование часового пояса.  Данное свойство в настоящий момент не поддерживается.|"short", "long"|Данное свойство в настоящий момент не поддерживается.|  
  
 Значения по умолчанию для свойств `weekday`, `era`, `year`, `month`, `day`, `hour`, `minute` и `second` — `undefined`.  Если эти свойства не заданы, для свойств `year`, `month` и `day` используется форматирование типа "numeric".  
  
 Все языковые стандарты должны поддерживать по крайней мере следующие форматы:  
  
-   день недели, год, месяц, день, час, минута, секунда;  
  
-   день недели, год, месяц, день;  
  
-   год, месяц, день;  
  
-   год, месяц;  
  
-   месяц, день;  
  
-   час, минута, секунда;  
  
-   час, минута.  
  
## Свойства  
 В следующей таблице перечислены свойства объекта `DateTimeFormat`.  
  
|||  
|-|-|  
|Свойство|Описание|  
|[constructor](../../javascript/reference/constructor-property-intl-datetimeformat.md)|Указывает функцию, создающую объект средства форматирования даты и времени.|  
|[format](../../javascript/reference/format-property-intl-datetimeformat.md)|Возвращает функцию, которая форматирует дату, соответствующую языковому стандарту, используя параметры средства форматирования даты и времени.|  
|[prototype](../../javascript/reference/prototype-property-intl-datetimeformat.md)|Возвращает ссылку на прототип для средства форматирования даты и времени.|  
  
## Методы  
 В следующей таблице перечислены методы объекта `DateTimeFormat`.  
  
|||  
|-|-|  
|Метод|Описание|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-datetimeformat.md)|Возвращает объект, содержащий свойства и значения объекта средства форматирования даты и времени.|  
  
## Пример  
 В следующем примере показан результат передачи объекта Date в объект `DateTimeFormat` с использованием различных языковых стандартов.  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
if (console && console.log) {  
    console.log(new Intl.DateTimeFormat("en-US").format(date));  
    // Returns ‎2‎/‎1‎/‎2013  
    console.log(new Intl.DateTimeFormat("ja-JP").format(date));  
    // Returns ‎2013‎年‎2‎月‎1‎日  
    console.log(new Intl.DateTimeFormat("ar-SA", options).format(date));  
    // Returns ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
    console.log(new Intl.DateTimeFormat("hi-IN", options).format(date));  
    // Returns ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
}  
```  
  
## Пример  
 В следующем примере создается объект `DateTimeFormat`, задающий текущий день недели в длинном формате с использованием языкового стандарта "Арабский \(Саудовская Аравия\)", исламского календаря и латинской системы нумерации.  
  
```javascript  
var dtf = new Intl.DateTimeFormat(["ar-SA-u-ca-islamic-nu-latn"], {  
    weekday: "long",  
    year: "numeric",  
    day: "numeric",  
    month: "long"  
});   
  
If (console && console.log) {  
    console.log(dtf.format(new Date()));  
    // Returns ‏الجمعة‏, ‏19‏ ‏رمضان‏, ‏1434  
}  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## См. также  
 [toLocaleString \(Date\)](../../javascript/reference/tolocalestring-date.md)   
 [Метод toLocaleDateString \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)   
 [Метод toLocaleTimeString \(Date\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)   
 [Объект Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md)   
 [Объект Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)