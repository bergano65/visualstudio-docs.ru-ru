---
title: "Свойство length (аргументы) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Length - свойство"
  - "length - свойство (аргументы)"
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Свойство length (аргументы) (JavaScript)
Возвращает фактическое количество аргументов, переданных функции вызывающим объектом.  
  
## Синтаксис  
  
```  
[function.]arguments.length  
```  
  
## Заметки  
 Необязательный аргумент *function* — это имя выполняемого в данный момент объекта `Function`  
  
 При инициализации свойства **length** объекта **arguments** обработчик скриптов присваивает ему фактическое число аргументов, переданных объекту `Function` при начале выполнения этой функции.  
  
## Пример  
 В следующем примере демонстрируется использование свойства **length** объекта **arguments**.  Для полного понимания примера следует передать функции больше аргументов, чем 2 ожидаемых.  
  
```javascript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Относится к**: [Объект arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Объект Function](../../javascript/reference/function-object-javascript.md)  
  
## См. также  
 [Свойство arguments \(Function\)](../../javascript/reference/arguments-property-function-javascript.md)   
 [Свойство length \(массив\)](../../javascript/reference/length-property-array-javascript.md)   
 [Свойство length \(строка\)](../../javascript/reference/length-property-string-javascript.md)