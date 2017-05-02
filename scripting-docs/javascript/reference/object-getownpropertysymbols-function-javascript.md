---
title: "Функция Object.getOwnPropertySymbols (JavaScript) | Microsoft Docs"
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Функция Object.getOwnPropertySymbols (JavaScript)
Возвращает собственные символьные свойства объекта.  Собственные символьные свойства объекта — это свойства, которые определяются в самом объекте, а не наследуются им от прототипа.  
  
## Синтаксис  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### Параметры  
 `object`  
 Обязательный.  Объект, содержащий собственные символы.  
  
## Возвращаемое значение  
 Массив, содержащий собственные символы объекта.  
  
## Заметки  
 Для получения символьных свойств объекта используйте функцию `Object.getOwnPropertySymbols`.  Функция `Object.getOwnPropertyNames` не возвращает символьные свойства.  
  
## Пример  
 В следующем примере кода показано, как получить символьные свойства объекта.  
  
```javascript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(s[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]