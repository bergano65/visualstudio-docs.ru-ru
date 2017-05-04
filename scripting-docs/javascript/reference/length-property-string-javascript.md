---
title: "Свойство length (строка) (JavaScript) | Microsoft Docs"
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
  - "строки [Visual Studio], длина"
  - "Length - свойство"
  - "length - свойство (строка)"
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Свойство length (строка) (JavaScript)
Возвращает длину объекта `String`.  
  
> [!WARNING]
>  Строки JavaScript являются неизменяемыми, поэтому длину строки нельзя изменить.  
  
## Синтаксис  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## Заметки  
 Свойство `length` содержит целое число, которое определяет количество знаков в объекте `String`.  Индекс последнего знака объекта `String` равен `length` \- 1.  
  
## Пример  
 Следующий код показывает, как использовать метод `length`.  Строки JavaScript являются неизменяемыми и не могут быть изменены на месте.  Однако можно записать инвертированную строку в массив, а затем вызвать `join` с пустым символом, чтобы создать строку без символа\-разделителя.  
  
```javascript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]