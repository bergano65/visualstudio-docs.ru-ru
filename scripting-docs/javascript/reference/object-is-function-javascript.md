---
title: "Функция Object.is (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 6e2f6c6d-7cd2-47c4-a513-3ba53988d27d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Функция Object.is (JavaScript)
Возвращает значение, определяющее, совпадают ли два значения.  
  
## Синтаксис  
  
```javascript  
Object.is(value1, value2)  
```  
  
#### Параметры  
 `value1`  
 Обязательный.  Первое значение для проверки.  
  
 `value2`  
 Обязательный.  Второе значение для проверки.  
  
## Возвращаемое значение  
 Значение `true`, если значения совпадают; в противном случае — значение `false`.  
  
## Заметки  
 В отличие от оператора \=\=, функция `Object.is` не приводит проверяемые значения к каким\-либо типам.  
  
 Функция `Object.is` применяет такое же сравнение, что и оператор \=\=\=, за исключением случаев, когда `Object.is` считает, что значение `Number.isNaN` совпадает со значением `NaN`.  Кроме того, она обрабатывает \+0 и –0 как разные значения.  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]