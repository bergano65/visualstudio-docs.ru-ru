---
title: "Свойство input ($_) (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$_"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "$_ - свойство"
  - "input - свойство"
ms.assetid: 88c6d1d8-56f7-4334-a7eb-e899aec9cda4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Свойство input ($_) (RegExp) (JavaScript)
Возвращает строку, в которой выполнялся поиск регулярного выражения.  Только для чтения.  
  
## Синтаксис  
  
```  
  
RegExp.input  
```  
  
## Заметки  
 Объект, связанный с данным свойством, всегда является глобальным объектом `RegExp`.  
  
 Значение свойства **input** изменяется при каждом редактировании строки, в которой выполняется поиск.  
  
 В следующем примере демонстрируется использование свойства **input**.  
  
```javascript  
function inputDemo(){  
   var s;  
   var re = new RegExp("d(b+)(d)","ig");  
   var str = "cdbBdbsbdbdz";  
   var arr = re.exec(str);  
   s = "The string used for the match was " + RegExp.input;   
   return(s);  
}  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект RegExp](../../javascript/reference/regexp-object-javascript.md)  
  
## См. также  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)