---
title: "Свойство length (функция) (JavaScript) | Microsoft Docs"
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
  - "length - свойство (функция)"
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Свойство length (функция) (JavaScript)
Получает количество аргументов, определенных для функции.  
  
## Синтаксис  
  
```  
  
functionName.length  
```  
  
## Заметки  
 Необходимое имя *functionName* представляет собой имя функции.  
  
 Обработчик сценариев инициализирует свойство **length** функции числом аргументов в определении функции, когда создается экземпляр функции.  
  
 Поведение функции при ее вызове с числом аргументов, отличным от значения его свойства **length**, зависит от данной функции.  
  
## Пример  
 В следующем примере показано использование свойства **length**.  
  
```javascript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## См. также  
 [Свойство arguments \(Function\)](../../javascript/reference/arguments-property-function-javascript.md)   
 [Свойство length \(массив\)](../../javascript/reference/length-property-array-javascript.md)   
 [Свойство length \(строка\)](../../javascript/reference/length-property-string-javascript.md)