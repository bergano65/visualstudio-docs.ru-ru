---
title: "Объект RegExp (JavaScript) | Microsoft Docs"
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
  - "RegExp"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "RegExp - объект"
  - "RegExp - объект, общие сведения"
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Объект RegExp (JavaScript)
Встроенный глобальный объект, в котором хранится информация о результатах совпадений шаблона регулярного выражения.  
  
## Синтаксис  
  
```  
  
RegExp.property   
```  
  
## Заметки  
 Обязательный аргумент *property* может быть любым из свойств объекта `RegExp`.  
  
 Объект `RegExp` нельзя создать напрямую, но он всегда доступен для использования.  До успешного завершения поиска регулярного выражения начальные значения различных свойств объекта `RegExp` таковы:  
  
|Свойство|Краткая форма|Начальное значение|  
|--------------|-------------------|------------------------|  
|index||\-1|  
|input|$\_|Пустая строка.|  
|lastIndex||\-1|  
|lastMatch|$&|Пустая строка.|  
|lastParen|$\+|Пустая строка.|  
|leftContext|$\`|Пустая строка.|  
|rightContext|$'|Пустая строка.|  
|$1 \- $9|$1 \- $9|Пустая строка.|  
  
 Его свойства имеют значение undefined, пока поиск регулярного выражения не будет завершен успешно.  
  
 Глобальный объект `RegExp` не следует путать с объектом **Regular Expression**.  Несмотря на сходство, они совершенно различны.  Свойства глобального объекта `RegExp` содержат постоянно обновляемые данные о каждом найденном совпадении, тогда как свойства объекта **Regular Expression** содержат данные только о совпадениях внутри этого экземпляра **Regular Expression**.  
  
## Пример  
 В следующем примере выполняется поиск регулярного выражения.  Отображаются совпадения и подсовпадения из глобального объекта `RegExp` и из массива, возвращаемого методом `exec`.  
  
```javascript  
var newLine = "<br />";  
  
var re = /(\w+)@(\w+)\.(\w+)/g  
var src = "Please send mail to george@contoso.com and someone@example.com. Thanks!"  
  
var result;  
var s = "";  
  
// Get the first match.  
result = re.exec(src);  
  
while (result != null) {  
    // Show the entire match.  
    s += newLine;  
  
    // Show the match and submatches from the RegExp global object.  
    s += "RegExp.lastMatch: " + RegExp.lastMatch + newLine;  
    s += "RegExp.$1: " + RegExp.$1 + newLine;  
    s += "RegExp.$2: " + RegExp.$2 + newLine;  
    s += "RegExp.$3: " + RegExp.$3 + newLine;  
  
    // Show the match and submatches from the array that is returned  
    // by the exec method.  
    for (var index = 0; index < result.length; index++) {  
        s +=  index + ": ";  
        s += result[index];  
        s += newLine;  
    }  
  
    // Get the next match.  
    result = re.exec(src);  
}  
document.write(s);  
  
// Output:  
//  RegExp.lastMatch: george@contoso.com  
//  RegExp.$1: george  
//  RegExp.$2: contoso  
//  RegExp.$3: com  
//  0: george@contoso.com  
//  1: george  
//  2: contoso  
//  3: com  
  
//  RegExp.lastMatch: someone@example.com  
//  RegExp.$1: someone  
//  RegExp.$2: example  
//  RegExp.$3: com  
//  0: someone@example.com  
//  1: someone  
//  2: example  
//  3: com  
  
```  
  
<a name="js56jsobjregexpprop"></a>   
## Свойства  
 [Свойства $1...$9](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md) &#124; [Свойство index](../../javascript/reference/index-property-regexp-javascript.md) &#124; [Свойство input](../../javascript/reference/input-property-dollar-regexp-javascript.md) &#124; [Свойство lastIndex](../../javascript/reference/lastindex-property-regexp-javascript.md) &#124; [Свойство lastMatch](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md) &#124; [Свойство lastParen](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md) &#124; [Свойство leftContext](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md) &#124; [Свойство rightContext](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## Методы  
 Объект `RegExp` не имеет методов.  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## См. также  
 [Объект Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Объект String](../../javascript/reference/string-object-javascript.md)