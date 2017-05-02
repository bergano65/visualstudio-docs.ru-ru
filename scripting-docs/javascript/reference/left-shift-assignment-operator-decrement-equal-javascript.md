---
title: "Оператор присваивания сдвига влево (&lt;&lt;=) (JavaScript) | Microsoft Docs"
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
  - "<<="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "оператор <<= [JavaScript]"
  - "оператор присваивания сдвига влево (<<=) [JavaScript]"
  - "операторы сдвига влево [JavaScript]"
  - "операторы присваивания, JavaScript"
ms.assetid: 9f30ff46-48cc-4931-b260-edef31ff0076
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Оператор присваивания сдвига влево (&lt;&lt;=) (JavaScript)
Перемещает на указанное число битов влево и присваивает результат `result`.  Освобожденные операцией биты заполняются нулями.  
  
## Синтаксис  
  
```  
  
result <<= expression  
```  
  
## Параметры  
 `result`  
 Любая переменная.  
  
 `expression`  
 Количество битов, на которое следует выполнить перемещение.  
  
## Заметки  
 Использование оператора `<<=` полностью эквивалентно следующему выражению `result = result << expression`.  
  
 В следующем примере показано, как использовать оператор `<<=`.  
  
```javascript  
// 14 is 00000000000000000000000000001110  
var temp = 14;  
temp <<= 2;   
document.write(temp);  
// 56 is 00000000000000000000000000111000  
Output: 56  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор побитового сдвига влево \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Оператор побитового сдвига вправо \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Оператор сдвига вправо без знака \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)