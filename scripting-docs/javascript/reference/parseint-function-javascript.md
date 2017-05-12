---
title: "Функция parseInt (JavaScript) | Microsoft Docs"
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
  - "parseInt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "parseInt - метод"
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Функция parseInt (JavaScript)
Преобразует строку в целочисленное значение.  
  
## Синтаксис  
  
```  
parseInt(numString, [radix])   
```  
  
## Параметры  
 `numString`  
 Обязательный.  Строка, которую требуется преобразовать в число.  
  
 `radix`  
 Необязательный.  Значение в интервале от 2 до 36, указывающее базу для числа в `numString`.  Если этот аргумент не указан, то строки с префиксом "0x" считаются шестнадцатеричными числами.  Все остальные строки считаются десятичными числами.  
  
## Заметки  
 Функция `parseInt` возвращает целое значение, равное числу, содержащемуся в строке `numString`.  Если никакую начальную часть строки `numString` не удается преобразовать в целое число, возвращается значение `NaN` \(не число\).  
  
```javascript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 Проверить результат на наличие значения `NaN` можно с помощью функции `isNaN`.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Global](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  Начиная с [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], функция `parseInt` не обрабатывает строку с префиксом "0" как восьмеричное число.  Однако если функция `parseInt` не используется, строки с префиксом "0" по\-прежнему могут интерпретироваться как восьмеричные числа.  Дополнительные сведения о восьмеричных целых числах см. в разделе [Типы данных](../../javascript/data-types-javascript.md).  
  
## См. также  
 [Функция isNaN](../../javascript/reference/isnan-function-javascript.md)   
 [Функция parseFloat](../../javascript/reference/parsefloat-function-javascript.md)   
 [Объект String](../../javascript/reference/string-object-javascript.md)   
 [Метод valueOf \(Object\)](../../javascript/reference/valueof-method-object-javascript.md)