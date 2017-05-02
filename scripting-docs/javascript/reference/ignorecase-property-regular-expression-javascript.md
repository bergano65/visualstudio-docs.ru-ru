---
title: "Свойство ignoreCase (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "ignoreCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "IgnoreCase - свойство"
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Свойство ignoreCase (Regular Expression) (JavaScript)
Возвращает логическое значение, указывающее состояние флага ignoreCase \(**i**\), используемого с регулярным выражением.  Значение по умолчанию — **false**.  Только для чтения.  
  
## Синтаксис  
  
```  
  
rgExp.ignoreCase  
```  
  
## Заметки  
 Обязательная ссылка `rgExp` — экземпляр объекта `RegExp`.  
  
 Свойство **ignoreCase** возвращает значение **true**, если для регулярного выражения установлен флаг ignoreCase, и значение **false**, если этот флаг не установлен.  
  
 Флаг ignoreCase используется для указания того, что при поиске соответствия шаблону в строке не следует учитывать регистр знаков.  
  
## Пример  
 В следующем примере демонстрируется использование свойства **ignoreCase**.  Если передать в показанную ниже функцию значение "gi", то все вхождения слова "the" будут заменены на слово "a", в том числе первое вхождение "The".  Это объясняется тем, что при установке флага ignoreCase поиск ведется без учета регистра.  Поэтому буквы "T" и "t" считаются одинаковыми.  
  
 Эта функция возвращает логические значения, которые указывают состояние допустимых флагов регулярного выражения: **g**, **i** и **m**.  Кроме того, эта функция возвращает строку, в которой выполнены все замены.  
  
```javascript  
function RegExpPropDemo(flag){  
    // The flag parameter is a string that contains  
    // g, i, or m. The flags can be combined.  
  
    // Check flags for validity.  
    if (flag.match(/[^gim]/))  
        {  
        return ("Flag specified is not valid");  
        }  
  
    // Create the string on which to perform the replacement.  
    var orig = "The batter hit the ball with the bat ";  
    orig += "and the fielder caught the ball with the glove.";  
  
    // Replace "the" with "a".  
    var re = new RegExp("the", flag);  
    var r = orig.replace(re, "a");          
  
    // Output the resulting string and the values of the flags.  
    var s = "";  
    s += "global: " + re.global.toString();  
    s += "<br />";  
    s += "ignoreCase: " + re.ignoreCase.toString();  
    s += "<br />";  
    s += "multiline: " + re.multiline.toString();  
    s += "<br />";  
    s += "Resulting String: " + r;  
    s += "<br />";  
    s += "<br />";  
    return (s);  
}  
  
document.write(RegExpPropDemo("gi"));  
document.write(RegExpPropDemo("g"));  
```  
  
## Пример  
 Ниже показан результат.  
  
```javascript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Относится к**: [Объект Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## См. также  
 [Свойство global \(Regular Expression\)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [Свойство multiline \(Regular Expression\)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)