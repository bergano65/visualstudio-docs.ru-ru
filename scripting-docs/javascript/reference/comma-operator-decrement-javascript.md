---
title: "Оператор &quot;запятая&quot; (,) (JavaScript) | Microsoft Docs"
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
  - "%2C"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "оператор "запятая""
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Оператор &quot;запятая&quot; (,) (JavaScript)
Приводит к последовательному выполнению двух выражений.  
  
## Синтаксис  
  
```  
  
expression1, expression2  
```  
  
## Параметры  
 `expression1`  
 Произвольное выражение.  
  
 `expression2`  
 Произвольное выражение.  
  
## Заметки  
 Оператор `,` приводит к выполнению выражений в порядке слева направо.  Чаще всего оператор `,` применяется в выражении инкремента для цикла `for`.  Примеры.  
  
```javascript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 Оператор `for` позволяет выполнить только одно выражение в конце каждого прохода цикла.  Оператор `,` позволяет использовать несколько выражений как одно выражение, поэтому можно применить инкремент к обеим переменным.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор for](../../javascript/reference/for-statement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)