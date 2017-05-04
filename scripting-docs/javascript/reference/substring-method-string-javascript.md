---
title: "Метод substring (String) (JavaScript) | Microsoft Docs"
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
  - "substring"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "подстроки"
  - "substring - метод"
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Метод substring (String) (JavaScript)
Возвращает подстроку, расположенную в указанном месте объекта `String`.  
  
## Синтаксис  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## Параметры  
 `start`  
 Обязательный.  Целое значение индекса \(начиная с нуля\), указывающее начало подстроки.  
  
 `end`  
 Необязательный.  Целое значение индекса \(начиная с нуля\), указывающее конец подстроки.  Подстрока включает символы до символа, задаваемого значением `end`, но не включая его.  
  
 Если значение `end` опущено, будут возвращены символы от позиции `start` до конца исходной строки.  
  
## Заметки  
 Метод `substring` возвращает строку, содержащую подстроку, которая начинается с позиции `start` и завершается позицией `end` \(но не включает эту позицию\).  
  
 В качестве начальной позиции подстроки метод **substring** использует наименьшее значение аргументов `start` и `end`.  Например, вызовы strvar.substring\(0, 3**\)** и strvar.substring\(3, 0\) возвращают одну и ту же подстроку.  
  
 Если значение `start` или `end` равно `NaN` или является отрицательным числом, оно заменяется нулем.  
  
 Длина подстроки равна абсолютному значению разности аргументов `start` и `end`.  Например, длина подстроки, возвращаемой вызовами strvar.substring\(0, 3\) и strvar.substring\(3, 0\), равна 3.  
  
## Пример  
 В следующем примере показано использование метода **substring**.  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Метод substr \(String\)](../../javascript/reference/substr-method-string-javascript.md)