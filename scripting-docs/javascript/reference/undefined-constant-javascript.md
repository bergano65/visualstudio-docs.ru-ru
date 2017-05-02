---
title: "Константа undefined (JavaScript) | Microsoft Docs"
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
  - "undefined"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "undefined - свойство"
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Константа undefined (JavaScript)
Значение, которое не было определено, например переменная, которая не была инициализирована.  
  
## Синтаксис  
  
```  
undefined  
```  
  
## Заметки  
 Константа `undefined` является членом объекта `Global` и становится доступной при инициализации обработчика скриптов.  Если переменная объявлена, но не инициализирована, ее значение равно **undefined**.  
  
 Если переменная не объявлена, ее нельзя сравнить с константой `undefined`, однако можно сравнить тип переменной со строкой "undefined".  
  
 Константу `undefined` удобно использовать для явной проверки равенства переменной значению "undefined" или для задания для нее этого значения.  
  
## Пример  
 В следующем примере показано, как использовать константу `undefined`.  
  
```javascript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## Требования  
 Свойство `undefined` было введено в [!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)]. В [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)] это свойство стало доступно только на чтение.  
  
 **Относится к**: [Объект Global](../../javascript/reference/global-object-javascript.md)  
  
## См. также  
 [Оператор typeof](../../javascript/reference/typeof-operator-decrementjavascript.md)