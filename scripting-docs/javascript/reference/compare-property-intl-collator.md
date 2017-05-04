---
title: "Свойство compare (Intl.Collator) | Microsoft Docs"
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
ms.assetid: 59f274dc-6e52-4344-8d5c-b9f0000b66e0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Свойство compare (Intl.Collator)
Возвращает функцию, которая сравнивает две строки с использованием порядка сортировки средства упорядочения.  
  
## Синтаксис  
  
```javascript  
collatorObj.compare  
```  
  
#### Параметры  
 `collatorObj`  
 Обязательное.  имя объекта `Collator`, который надо использовать для сравнения.  
  
## Заметки  
 Функция, возвращаемая свойством `compare`, принимает два аргумента — `x` и `y` — и возвращает результат сравнения `x` и `y` для конкретного языкового стандарта с использованием параметров, заданных в объекте `Collator`.  
  
 Результат сравнения:  
  
-   \-1 если `x` до `y` в порядке сортировки.  
  
-   ноль \(0\) если `x` равно `y` в порядке сортировки.  
  
-   1 если `x` после `y` в порядке сортировки.  
  
## Пример  
 В следующем примере создается объект `Collator` и выполняется сравнение.  
  
```javascript  
var co = new Intl.Collator(["de-DE-u-co-phonebk"]);  
  
if (console && console.log) {  
    console.log(co.compare("a", "b")); // Returns -1  
}  
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
 В следующем примере объект `Collator` используется для поиска строки.  
  
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
 [Объект Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md)