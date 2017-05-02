---
title: "Объект JSON (JavaScript) | Microsoft Docs"
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
  - "JSON"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JSON - объект"
ms.assetid: 0279a0e0-70bf-451a-a78e-0da4e2fdeb9a
caps.latest.revision: 43
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 43
---
# Объект JSON (JavaScript)
Встроенный объект, предоставляющий функции для преобразования значений [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] в формат JSON \(нотация объектов JavaScript\) и обратно.  Функция `JSON.stringify` сериализует значение [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] в текст JSON.  Функция `JSON.parse` десериализует текст JSON для получения значения [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Синтаксис  
  
```  
  
JSON.[method]  
  
```  
  
## Параметры  
 `Method`  
 Обязательный.  Имя одного из методов объекта `JSON`.  
  
## Заметки  
 Создать объект `JSON` с помощью оператора `new` невозможно.  При попытке это сделать возникает ошибка.  Тем не менее можно переопределить или изменить объект `JSON`.  
  
 Обработчик скриптов создает объект `JSON` при загрузке обработчика.  Скрипту всегда доступны его методы.  
  
 При использовании встроенного объекта `JSON` следите за тем, чтобы он не был переопределен другим объектом `JSON`, определенным в скрипте.  Может потребоваться изменить существующие операторы скрипта, которые обнаруживают наличие объекта `JSON`, поскольку у этих операторов будет другой результат вычисления.  Это показано в следующем примере.  
  
```javascript  
if (!this.JSON) {  
    // JSON object does not exist.  
    }  
```  
  
 В примере выше результатом `!this.JSON` в [!INCLUDE[jsv58text](../../javascript/reference/includes/jsv58text-md.md)] является значение false.  Поэтому код внутри оператора `if` не выполняется.  
  
## Функции  
 [Функция JSON.parse](../../javascript/reference/json-parse-function-javascript.md)  
  
 [Функция JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)  
  
## Требования  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## См. также  
 [Метод toJSON \(Date\)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Объекты JavaScript](../../javascript/reference/javascript-objects.md)   
 [Пример шаблона приложения Hub \(Магазин Windows\)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)