---
title: "Оператор побитового сдвига влево (&lt;&lt;) (JavaScript) | Microsoft Docs"
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
  - "<<"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "<< - оператор"
  - "<< - оператор, сведения об операторе <<"
  - "побитовые операторы, оператор сдвига влево"
  - "операторы сдвига влево"
ms.assetid: 18148596-7b86-4add-aeef-106991c69435
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Оператор побитового сдвига влево (&lt;&lt;) (JavaScript)
Сдвигает влево биты выражения.  
  
## Синтаксис  
  
```  
  
result = expression1 << expression2  
```  
  
## Параметры  
 *result*  
 Любая переменная.  
  
 *expression1*  
 Произвольное выражение.  
  
 *expression2*  
 Произвольное выражение.  
  
## Заметки  
 Оператор **\<\<** сдвигает биты выражения *expression1* влево на количество бит, указанное в выражении *expression2*.  Примеры.  
  
```javascript  
var temp  
temp = 14 << 2  
```  
  
 Переменная *temp* имеет значение 56, поскольку при сдвиге значения 14 \(00001110 в двоичном выражении\) на два бита влево получается значение 56 \(00111000 в двоичном выражении\).  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор присваивания сдвига влево \(\<\<\=\)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)   
 [Оператор побитового сдвига вправо \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Оператор сдвига вправо без знака \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)