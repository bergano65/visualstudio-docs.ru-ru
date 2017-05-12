---
title: "Свойство lastMatch ($&amp;) (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$&"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastMatch - свойство ($%)"
  - "lastMatch - свойство ($&)"
ms.assetid: d223836d-5235-48a5-a926-d20764ad3f14
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Свойство lastMatch ($&amp;) (RegExp) (JavaScript)
Возвращает знаки последнего соответствия, найденного при поиске регулярного выражения.  Только для чтения.  
  
## Синтаксис  
  
```  
  
RegExp.lastMatch  
```  
  
## Заметки  
 Объект, связанный с данным свойством, всегда является глобальным объектом `RegExp`.  
  
 Начальным значением свойства `lastMatch` является пустая строка.  Значение свойства `lastMatch` изменяется при каждом обнаружении искомого выражения.  
  
## Пример  
 В следующем примере показано использование свойства `lastMatch`.  
  
```javascript  
// Create the regular expression pattern.  
var re = new RegExp("d(b+)(d)","ig");  
var str = "cdbBdbsbdbdz";  
  
// Perform the search.  
var arr = re.exec(str);  
  
// Print the output.  
var s = ""   
s += "$1: " + RegExp.$1 + "<br />";  
s += "$2: " + RegExp.$2 + "<br />";  
s += "$3: " + RegExp.$3 + "<br />";  
s += "input: " + RegExp.input + "<br />";  
s += "lastMatch: " + RegExp.lastMatch + "<br />";  
s += "leftContext: " + RegExp.leftContext + "<br />";  
s += "rightContext: " + RegExp.rightContext + "<br />";   
s += "lastParen: " + RegExp.lastParen + "<br />";  
  
document.write(s);  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Относится к**: [Объект RegExp](../../javascript/reference/regexp-object-javascript.md)  
  
## См. также  
 [Свойства $1...$9 \(RegExp\)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)   
 [Свойство index \(RegExp\)](../../javascript/reference/index-property-regexp-javascript.md)   
 [Свойство input \($\_\) \(RegExp\)](../../javascript/reference/input-property-dollar-regexp-javascript.md)   
 [Свойство lastIndex \(RegExp\)](../../javascript/reference/lastindex-property-regexp-javascript.md)   
 [Свойство lastParen \($\+\) \(RegExp\)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)   
 [Свойство leftContext \($\`\) \(RegExp\)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)   
 [Свойство rightContext \($'\) \(RegExp\)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)