---
title: "Свойство global (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "Global"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "global - свойство"
ms.assetid: 76a0f115-0d89-4aca-86d5-932895c6d649
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Свойство global (Regular Expression) (JavaScript)
Возвращает логическое значение, указывающее состояние глобального флага \(**g**\), используемого с регулярным выражением.  Значение по умолчанию — **false**.  Только для чтения.  
  
## Синтаксис  
  
```  
  
rgExp.global  
```  
  
## Заметки  
 Обязательная ссылка `rgExp` — экземпляр объекта **Regular Expression**.  
  
 Свойство `global` возвращает значение **true**, если для регулярного выражения установлен глобальный флаг, и значение **false**, если этот флаг не установлен.  
  
 Глобальный флаг означает, что при поиске следует найти все вхождения шаблона в строке, а не только первое вхождение.  Этот флаг также называется глобальным соответствием.  
  
## Пример  
 В следующем примере показано использование свойства `global`.  Если передать в показанную ниже функцию значение **g**, то все вхождения слова "the" будут заменены на слово "a".  Обратите внимание, что слово "The" в начале строки не заменяется, поскольку функции не передан флаг **i** \(не учитывать регистр\).  
  
 Эта функция отображает состояние свойств, связанных с допустимыми флагами регулярных выражений: **g**, **i** и **m**.  Кроме того, эта функция отображает строку, в которой выполнены все замены.  
  
```javascript  
function RegExpPropDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The batter hit the ball with the bat ";  
   ss += "and the fielder caught the ball with the glove.";  
  
   //Replace "the" with "a".  
   var re = new RegExp("the", flag);  
   var r = ss.replace(re, "a");          
  
   // Output the resulting string and the flags.  
   var s = "";  
   s += "global: " + re.global.toString();  
   s += "<br />";  
   s += "ignoreCase: " + re.ignoreCase.toString();  
   s += "<br />";  
   s += "multiline: " + re.multiline.toString();  
   s += "<br />";  
   s += "Resulting String: " + r;  
  
   return (s);  
}  
  
document.write(RegExpPropDemo("g"));  
```  
  
## Пример  
 Ниже показан результат.  
  
```javascript  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Относится к**: [Объект Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## См. также  
 [Свойство ignoreCase \(Regular Expression\)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Свойство multiline \(Regular Expression\)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)