---
title: "Метод join (Array) (JavaScript) | Microsoft Docs"
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
  - "join"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Join - метод"
  - "сцепление строк, метод join"
  - "массивы [Visual Studio], соединение"
ms.assetid: 20f8fde1-014b-488e-9008-464a86e6b21f
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Метод join (Array) (JavaScript)
Объединяет все элементы массива, вставляя между ними заданную строку\-разделитель.  
  
## Синтаксис  
  
```  
  
arrayObj.join([separator])   
```  
  
## Параметры  
 `arrayObj`  
 Обязательный.  Объект `Array`.  
  
 `separator`  
 Необязательный.  Строка, используемая для отделения одного элемента массива от следующего в результирующем объекте `String`.  Если этот аргумент опущен, элементы массива разделяются запятыми.  
  
## Заметки  
 Если какой\-либо из элементов массива имеет значение **undefined** или `null`, он обрабатывается как пустая строка.  
  
## Пример  
 В следующем примере кода показано использование метода **join**.  
  
```javascript  
var a, b;  
a = new Array(0,1,2,3,4);  
b = a.join("-");  
document.write(b);  
  
// Output:  
// 0-1-2-3-4  
  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## См. также  
 [Объект String](../../javascript/reference/string-object-javascript.md)