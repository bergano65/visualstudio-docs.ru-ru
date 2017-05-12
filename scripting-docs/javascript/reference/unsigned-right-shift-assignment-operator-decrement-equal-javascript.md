---
title: "Оператор присваивания сдвига вправо без учета знака (&gt;&gt;&gt;=) (JavaScript) | Microsoft Docs"
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
  - ">>>="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>>= - оператор"
  - "операторы присваивания, JavaScript"
  - "оператор присваивания сдвига вправо без знака (>>>=)"
ms.assetid: f67c3737-7d39-41ae-9c11-8b16d38f6179
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Оператор присваивания сдвига вправо без учета знака (&gt;&gt;&gt;=) (JavaScript)
Сдвигает значение переменной вправо на количество битов, указанное в значении выражения, не сохраняя знака, и присваивает результат переменной.  
  
## Синтаксис  
  
```  
  
result >>>= expression  
```  
  
## Параметры  
 *result*  
 Любая переменная.  
  
 *expression*  
 Произвольное выражение.  
  
## Заметки  
 Использование оператора \>\>\>\= полностью эквивалентно следующей операции:  
  
```javascript  
result = result >>> expression  
```  
  
 Оператор **\>\>\>\=** смещает вправо биты переменной *result* на количество битов, указанное в выражении *expression*.  Слева добавляются нули.  Цифры, сдвинутые за пределы диапазона, удаляются.  Примеры.  
  
```javascript  
var temp  
temp = -14  
temp >>>= 2  
```  
  
 Начальное значение переменной *temp* равно \-14 \(11111111 11111111 11111111 11110010 в двоичной записи с дополнением до двух\).  При смещении значения на два бита вправо получается значение 1073741820 \(00111111 11111111 11111111 11111100 в двоичной записи\).  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор сдвига вправо без знака \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Оператор побитового сдвига влево \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Оператор побитового сдвига вправо \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)