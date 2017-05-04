---
title: "Метод test (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "test"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "метод теста"
ms.assetid: 4f4b6e39-cb1a-4be9-a66f-7b846075580d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Метод test (Regular Expression) (JavaScript)
Возвращает логическое значение, указывающее, существует ли шаблон в строке, в которой выполняется поиск.  
  
## Синтаксис  
  
```  
  
rgExp.test(str)   
```  
  
## Параметры  
 `rgExp`  
 Обязательный.  Экземпляр объекта **Regular Expression**, содержащий шаблон регулярного выражения и применимые флаги.  
  
 `str`  
 Обязательный.  Строка, в которой выполняется поиск.  
  
## Заметки  
 Метод **test** проверяет, существует ли шаблон в строке, и возвращает значение **true**, если шаблон существует, и **false** в противном случае.  
  
 Свойства глобального объекта `RegExp` не изменяются методом **test**.  
  
## Пример  
 В следующем примере показано использование метода **test**.  Чтобы использовать этот пример, передайте функции шаблон регулярного выражения и строку.  Функция проверит, присутствует ли шаблон регулярного выражения в строке, и возвратит строку, показывающую результаты поиска.  
  
```javascript  
function TestDemo(re, teststring)  
{  
   // Test string for existence of regular expression.  
   var found = re.test(teststring)  
  
   // Format the output.  
   var s = "";  
   s += "'" + teststring + "'"  
  
   if (found)  
      s += " contains ";  
   else  
      s += " does not contain ";  
  
   s += "'" + re.source + "'"  
   return(s);  
}  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## См. также  
 [Объект RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Объект Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)