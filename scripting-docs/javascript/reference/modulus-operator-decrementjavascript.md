---
title: "Оператор модуля (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "%"
dev_langs: 
  - "JavaScript"
  - "DHTML"
helpviewer_keywords: 
  - "оператор модуля, JavaScript"
  - "% - оператор [JavaScript]"
  - "Modulo - функция [JavaScript]"
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Оператор модуля (JavaScript)
Выполняет деление значения одного выражения на значение другого выражения и возвращает остаток.  
  
## Синтаксис  
  
```  
  
result = number1 % number2  
```  
  
## Аргументы  
 `result`  
 Любая переменная.  
  
 `number1`  
 Произвольное числовое выражение.  
  
 `number2`  
 Произвольное числовое выражение.  
  
## Заметки  
 Оператор модуля \(или остатка\) делит значение `number1` на значение `number2` и возвращает только остаток в качестве `result`.  Знак `result` совпадает со знаком `number1`.  Значение `result` находится между 0 и абсолютным значением `number2`.  
  
 В следующем примере кода показано, как использовать оператор модуля.  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)