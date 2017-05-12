---
title: "Оператор с идентификатором (JavaScript) | Microsoft Docs"
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
  - "labeled_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "continue - оператор"
  - "идентификаторы, операторы"
  - "labeled - оператор"
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Оператор с идентификатором (JavaScript)
Предоставляет идентификатор для оператора.  
  
## Синтаксис  
  
```  
  
      label :  
   statements   
```  
  
## Параметры  
 *label*  
 Обязательный.  Уникальный идентификатор, используемый для ссылки на оператор с меткой.  
  
 `statements`  
 Необязательный.  Один или несколько операторов, связанных с идентификатором *label*.  
  
## Заметки  
 Метки используются операторами **break** и **continue** для указания оператора, к которому применяются операторы **break** и **continue**.  
  
## Пример  
 В следующем коде оператор **continue** относится к циклу **for**, которому предшествует оператор `Inner:`.  Когда значение `j` равняется 24, оператор **continue** вызывает переход этого цикла **for** на следующую итерацию.  При значениях от 21 до 23 и от 25 до 30 выполняется вывод на каждой строке.  
  
```javascript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## См. также  
 [Оператор break](../../javascript/reference/break-statement-javascript.md)   
 [Оператор continue](../../javascript/reference/continue-statement-javascript.md)