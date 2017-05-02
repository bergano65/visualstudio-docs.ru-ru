---
title: "Оператор побитового сдвига вправо (&gt;&gt;) (JavaScript) | Microsoft Docs"
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
  - ">>"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">> - оператор"
  - ">> - оператор, сведения об операторе >>"
  - ">> - оператор, битовые массивы"
  - "побитовые операторы, оператор сдвига вправо"
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Оператор побитового сдвига вправо (&gt;&gt;) (JavaScript)
Сдвигает вправо биты выражения, сохраняя знак.  
  
## Синтаксис  
  
```  
  
result = expression1 >> expression2  
```  
  
## Параметры  
 *result*  
 Любая переменная.  
  
 *expression1*  
 Произвольное выражение.  
  
 *expression2*  
 Произвольное выражение.  
  
## Заметки  
 Оператор \>\> сдвигает вправо биты выражения *expression1* на количество бит, указанное в выражении *expression2*.  Для заполнения позиций слева используется бит знака значения *expression1*.  Цифры, сдвинутые за пределы диапазона, удаляются.  Например, после вычисления следующего кода переменная *temp* имеет значение \-4, поскольку при сдвиге значения \-14 \(11110010 в двоичном выражении\) на два бита в право получается значение \-4 \(11111100 в двоичном выражении\).  
  
```javascript  
var temp  
temp = -14 >> 2  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор побитового сдвига влево \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Оператор присваивания сдвига вправо \(\>\>\=\)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Оператор сдвига вправо без знака \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)