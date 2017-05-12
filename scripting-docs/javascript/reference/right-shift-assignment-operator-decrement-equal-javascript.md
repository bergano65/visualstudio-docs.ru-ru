---
title: "Оператор присваивания сдвига вправо (&gt;&gt;=) (JavaScript) | Microsoft Docs"
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
  - ">>="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>= - оператор [JavaScript]"
  - "операторы присваивания, JavaScript"
  - "операторы сдвига вправо [JavaScript]"
ms.assetid: 8c1f7f90-e3ac-42ee-94f2-5ccc47d7aef6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Оператор присваивания сдвига вправо (&gt;&gt;=) (JavaScript)
Сдвигает значение переменной вправо на количество битов, указанное в значении выражения, сохраняя знак, и присваивает результат переменной.  
  
## Синтаксис  
  
```  
  
result >>= expression  
```  
  
## Параметры  
 *result*  
 Любая переменная.  
  
 *expression*  
 Произвольное выражение.  
  
## Заметки  
 Использование оператора **\>\>\=** полностью эквивалентно следующему выражению:  
  
```javascript  
result = result >> expression  
```  
  
 Оператор **\>\>\=** смещает вправо биты переменной *result* на количество битов, указанное в выражении *expression*.  Для заполнения позиций слева используется бит знака значения *result*.  Цифры, сдвинутые за пределы диапазона, удаляются.  Например, после вычисления следующего кода переменная *temp* имеет значение \-4, поскольку при сдвиге значения 14 \(11110010 в двоичном выражении\) на два бита в право получается значение \-4 \(11111100 в двоичном выражении\).  
  
```javascript  
var temp  
temp = -14  
temp >>= 2  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор побитового сдвига влево \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Оператор побитового сдвига вправо \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Оператор сдвига вправо без знака \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)