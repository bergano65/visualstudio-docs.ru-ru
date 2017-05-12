---
title: "Рекурсия (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "функции, рекурсивные вызовы функции"
  - "рекурсивные процедуры"
  - "вызовы функции, рекурсивные"
ms.assetid: 885855a6-3838-457d-9eb4-cce1ccaa5a8d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Рекурсия (JavaScript)
Рекурсия — это важный метод программирования, позволяющий функции вызывать саму себя.  
  
## Пример рекурсии  
 В качестве одного из примеров можно привести расчет факториалов.  Факториал числа *n* вычисляется путем умножения 1 \* 2 \* 3 \*…  *n*.  В следующем примере показано, как подсчитать факториалы итерационно, т. е. с помощью цикла `while`, в котором вычисляется результат.  
  
```javascript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    var tmp = num;  
    while (num-- > 2) {  
        tmp *= num;  
    }  
    return tmp;  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```  
  
 Этот пример можно легко преобразовать в рекурсию.  Вместо вычисления значения с помощью цикла `while` можно просто снова вызвать функцию `factorial`, передав ей очередное меньшее значение.  Рекурсия останавливается, когда значение становится равным 1.  
  
```javascript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    // Otherwise, call this recursive procedure again.  
    else {  
        return (num * factorial(num - 1));  
    }  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```