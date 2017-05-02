---
title: "Свойство multiline (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "multiline"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "multiline - свойство"
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Свойство multiline (Regular Expression) (JavaScript)
Возвращает логическое значение, указывающее состояние флага "multiline" \(**m**\), используемого с регулярным выражением.  Значение по умолчанию — **false**.  Только для чтения.  
  
## Синтаксис  
  
```  
  
rgExp.multiline  
```  
  
## Заметки  
 Обязательный аргумент `rgExp` представляет собой экземпляр объекта `RegExp`.  
  
 Свойство **multiline** возвращает значение **true**, если для регулярного выражения установлен флаг "multiline", и значение **false**, если этот флаг не установлен.  Свойство **multiline** имеет значение **true**, если объект регулярного выражения был создан с флагом **m**.  
  
 Если свойство **multiline** имеет значение **false**, "^" соответствует позиции в начале строки, а "$" — позиции в конце строки.  Если свойство **multiline** имеет значение **true**, "^" соответствует позиции в начале строки, а также позиции, следующей за символом "\\n" или "\\r", а "$" — позиции в конце строки и позиции, предшествующей символу "\\n" или "\\r".  
  
## Пример  
 В следующем примере показано поведение свойства **multiline**.  Если показанной ниже функции передать значение "m", то слово "while" будет заменено словом "and".  Это объясняется тем, что задан флаг "multiline", а слово "while" встречается в начале строки после символа новой строки.  Флаг "multiline" позволяет вести поиск в многострочных строках.  
  
```javascript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Относится к**: [Объект Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## См. также  
 [Свойство global \(Regular Expression\)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [Свойство ignoreCase \(Regular Expression\)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)