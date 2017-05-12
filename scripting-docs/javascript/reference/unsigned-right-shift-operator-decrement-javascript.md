---
title: "Оператор сдвига вправо без учета знака (&gt;&gt;&gt;) (JavaScript) | Microsoft Docs"
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
  - ">>>"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>> - оператор"
  - "оператор сдвига вправо без знака (>>>)"
ms.assetid: df48bdfc-8741-46ab-b681-449da57ac95c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Оператор сдвига вправо без учета знака (&gt;&gt;&gt;) (JavaScript)
Сдвигает вправо биты выражения, не сохраняя знак.  
  
## Синтаксис  
  
```  
  
result = expression1 >>> expression2  
```  
  
## Параметры  
 *result*  
 Любая переменная.  
  
 *expression1*  
 Произвольное выражение.  
  
 *expression2*  
 Произвольное выражение.  
  
## Заметки  
 Оператор **\>\>\>** сдвигает вправо биты выражения *expression1* на количество бит, указанное в выражении *expression2*.  Слева добавляются нули.  Цифры, сдвинутые за пределы диапазона, удаляются.  Примеры.  
  
```javascript  
var temp  
temp = -14 >>> 2  
```  
  
 Начальное значение переменной *temp* равно \-14 \(11111111 11111111 11111111 11110010 в двоичном дополнительном коде\).  При сдвиге значения на два бита вправо получается значение 1073741820 \(00111111 11111111 11111111 11111100 в двоичном выражении\).  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор присваивания сдвига вправо без учета знака \(\>\>\>\=\)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Оператор побитового сдвига влево \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Оператор побитового сдвига вправо \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)