---
title: "Оператор new (JavaScript) | Microsoft Docs"
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
  - "new_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "new - оператор JavaScript"
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Оператор new (JavaScript)
Создает новый объект.  
  
## Синтаксис  
  
```  
new constructor ([arguments])   
```  
  
## Параметры  
 `constructor`  
 Обязательный.  Конструктор объекта.  Если конструктор не принимает аргументов, скобки можно опустить.  
  
 `arguments`  
 Необязательный.  Все аргументы, которые необходимо передать конструктору нового объекта.  
  
## Заметки  
 Оператор `new` выполняет следующие задачи.  
  
-   Создает объект, не содержащий членов.  
  
-   Вызывает конструктор для этого объекта, передавая указатель на вновь созданный объект в виде указателя `this`.  
  
-   Затем конструктор инициализирует объект в соответствии с аргументами, переданными конструктору.  
  
 Далее приведены примеры допустимого использования оператора **new**.  
  
```javascript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор function](../../javascript/reference/function-statement-javascript.md)