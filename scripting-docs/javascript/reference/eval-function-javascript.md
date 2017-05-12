---
title: "Функция eval (JavaScript) | Microsoft Docs"
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
  - "eval"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "eval - функция"
  - "синтаксический анализ, код"
  - "синтаксический анализатор"
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Функция eval (JavaScript)
Вычисляет код [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] и выполняет его.  
  
## Синтаксис  
  
```  
eval(codeString)   
```  
  
## Параметры  
 `codeString`  
 Обязательный.  Значение `String`, которое содержит допустимый код [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Заметки  
 Функция `eval` разрешает динамическое выполнение исходного кода [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 Строка `codeString` анализируется средством синтаксического анализа [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] и выполняется.  
  
 Код, переданный в функцию `eval`, выполняется в том же контексте, в котором вызывается функция `eval`.  
  
 По возможности используйте функцию [JSON.parse](../../javascript/reference/json-parse-function-javascript.md) для десериализации текста JSON.  Функция `JSON.parse` более безопасна и выполняется быстрее, чем функция `eval`.  
  
## Пример  
 В следующем примере кода для проверки даты инициализируется переменная `myDate`.  
  
```javascript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Global](../../javascript/reference/global-object-javascript.md)  
  
## См. также  
 [Объект String](../../javascript/reference/string-object-javascript.md)