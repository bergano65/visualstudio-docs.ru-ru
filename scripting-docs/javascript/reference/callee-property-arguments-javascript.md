---
title: "Свойство callee (arguments) (JavaScript) | Microsoft Docs"
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
  - "callee"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "callee - свойство"
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Свойство callee (arguments) (JavaScript)
Возвращает исполняемый объект `Function`, который является текстом тела указанного объекта `Function`.  
  
## Синтаксис  
  
```  
[function.]arguments.callee  
```  
  
## Заметки  
 Необязательный аргумент *function* — это имя выполняемого в данный момент объекта `Function`  
  
 Свойство `callee` является членом объекта **arguments**, который становится доступным только при выполнении связанной с ним функции.  
  
 Начальным значением свойства `callee` является выполняемый объект `Function`.  Это позволяет рекурсивно использовать анонимные функции.  
  
## Пример  
  
```javascript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Относится к**: [Объект arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Объект Function](../../javascript/reference/function-object-javascript.md)  
  
## См. также  
 [Свойство caller \(Function\)](../../javascript/reference/caller-property-function-javascript.md)