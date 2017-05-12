---
title: "Метод toJSON (Date) (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "toJSON - метод"
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# Метод toJSON (Date) (JavaScript)
Используется методом [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md), чтобы включить преобразование данных объекта для сериализации JSON \(нотация объектов JavaScript\).  
  
## Синтаксис  
  
```  
  
objectname.toJSON()  
```  
  
## Параметры  
 `objectname`  
 Обязательный.  Объект, для которого требуется сериализация JSON.  
  
## Заметки  
 Метод `toJSON` используется функцией `JSON.stringify`.  Функция `JSON.stringify` сериализует значение [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] в текст JSON.  Если метод `toJSON` предоставлен функции `JSON.stringify`, метод `toJSON` вызывается при вызове `JSON.stringify`.  
  
 Метод `toJSON` — это встроенный член объекта [Date](../../javascript/reference/date-object-javascript.md) [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Он возвращает строку даты в формате ISO для часового пояса UTC \(обозначается суффиксом Z\).  
  
 Можно переопределить метод `toJSON` для типа `Date` или определить метод `toJSON` для других типов объектов, чтобы обеспечить преобразование данных до сериализации JSON для определенного типа объектов.  
  
## Пример  
 В следующем примере метод `toJSON` используется для сериализации значения членов строк в верхний регистр.  Метод `toJSON` вызывается при вызове функции `JSON.stringify`.  
  
```javascript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
  
/* The value of jsonText is:  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## Пример  
 В следующем примере показано, как использовать метод `toJSON`, являющийся встроенным членом объекта [Date](../../javascript/reference/date-object-javascript.md).  
  
```javascript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## Требования  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)] **Относится к:** [объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Объект JSON](../../javascript/reference/json-object-javascript.md)   
 [Функция JSON.parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Функция JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)   
 [Методы JavaScript](../../javascript/reference/javascript-methods.md)