---
title: "Объект Intl.Collator (JavaScript) | Microsoft Docs"
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
  - "Collator"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: acbb9461-f956-4b5b-ae5f-6a47815ae15c
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Объект Intl.Collator (JavaScript)
Предоставляет сравнения строк, соответствующие языковому стандарту.  
  
## Синтаксис  
  
```  
collatorObj = new Intl.Collator([locales][, options])  
```  
  
#### Параметры  
 `collatorObj`  
 Обязательное.  Имя переменной, к которой нужно присвоить объект `Collator`.  
  
 `locales`  
 Необязательный параметр.  Массив строк языкового стандарта, которые содержат один или несколько тегов языка или языкового стандарта.  Если включить несколько строк языкового стандарта, нужно перечислить их в порядке убывания приоритета, чтобы первая запись была предпочитаемым языковым стандартом.  Если пропустить этот параметр, то используется языковой стандарт по умолчанию среды выполнения JavaScript.  Дополнительные сведения см. в разделе "Примечания".  
  
 `options`  
 Необязательный параметр.  Объект, содержащий одно или несколько свойств, определяющих параметры сравнения.  Дополнительные сведения см. в разделе "Заметки".  
  
## Заметки  
 Параметр `locales` должен соответствовать тегам языка или языкового стандарта [BCP 47](http://tools.ietf.org/html/rfc5646), таким как "en\-US" и "zh\-Hans\-CN".  Тег может включать язык, регион, страну и вариант.  Список языков, см. в разделе [Реестр подтегов языка IANA](http://go.microsoft.com/fwlink/p/?linkid=227303).  Примеры тегов языка, см. в разделе [Приложение А](http://tools.ietf.org/html/rfc5646#appendix-A) к BCP 47.  Для `Collator`, можно включить расширение \-u в строке языкового стандарта, чтобы указать одно или несколько из следующих расширений юникода:  
  
-   \-co для определения таблиц сортировки вариантов \(определяется языковым стандартом\): "*language*\-*region*\-u\-co\-*value*".  
  
-   \-kn, чтобы определить числовое сравнение: "*language*\-*region*\-u\-kn\-true&#124;false".  
  
-   –kf, чтобы определить, требуется ли сортировка сначала прописных символов или символов в нижнем регистре: "*language*\-*region*\-u\-kf\-upper&#124;lower&#124;false"\).  Данное расширение в настоящий момент не поддерживается.  
  
 Для задания числового сравнения можно задать расширение –kn в строке языкового стандарта или использовать свойство `numeric` в параметре `options`.  Если используется свойство `numeric`, значение –kn не применяется.  
  
 Параметр `options` может включать следующие свойства:  
  
-   `localeMatcher`.  Задает используемый алгоритм подбора языкового стандарта.  Возможные значения — "lookup" и "best fit".  Значением по умолчанию является "подбирается автоматически".  
  
-   `usage`.  Указывает цель сравнения — сортировка или поиск.  Возможные значения — "sort" и "search".  Значение по умолчанию — «сортировка».  
  
-   `sensitivity`.  Задает чувствительность средства упорядочения.  Возможные значения — "base", "accent", "case" и "variant".  Значение по умолчанию — `undefined`.  
  
-   `ignorePunctuation`.  Указывает, игнорируются ли знаки препинания в сравнении.  Возможны следующие значения: "true" и "false".  Значение по умолчанию — `false`.  
  
-   `numeric`.  Указывает, используется ли числовая сортировка.  Возможны следующие значения: "true" и "false".  Значение по умолчанию — `false`.  
  
-   `caseFirst`.  В настоящий момент не поддерживается.  
  
## Свойства  
 В следующей таблице перечислены свойства объекта `Collator`.  
  
|||  
|-|-|  
|Свойство|Описание|  
|[compare](../../javascript/reference/compare-property-intl-collator.md)|Возвращает функцию, которая сравнивает две строки с использованием порядка сортировки средства упорядочения.|  
|[Конструктор](../../javascript/reference/constructor-property-intl-collator.md)|Указывает функцию, которая создает средство упорядочения.|  
|[прототип](../../javascript/reference/prototype-property-intl-collator.md)|Возвращает ссылку на прототип для средства упорядочения.|  
  
## Методы  
 В следующей таблице перечислены методы объекта `Collator`.  
  
|||  
|-|-|  
|Метод|Описание|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-collator.md)|Возвращает объект, содержащий свойства и значения средства упорядочения.|  
  
## Пример  
 В следующем примере создается объект `Collator` и выполняется сравнение.  
  
```javascript  
var co = new Intl.Collator(["de-DE"]);  
co.compare("a", "b"); // Returns -1  
  
```  
  
## Пример  
 В следующем примере объекты `Collator` используются для сортировки массива.  В этом примере показаны различия, связанные с языковым стандартом.  
  
```javascript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## Пример  
 В следующем примере объект `Collator` используется для поиска строки с заданием параметров сравнения.  
  
```javascript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## См. также  
 [Метод localeCompare \(String\)](../../javascript/reference/localecompare-method-string-javascript.md)   
 [Объект Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)   
 [Объект Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)