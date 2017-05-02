---
title: "Метод hasOwnProperty (Object) (JavaScript) | Microsoft Docs"
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
  - "hasOwnProperty"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "hasOwnProperty - метод"
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Метод hasOwnProperty (Object) (JavaScript)
Определяет, имеет ли объект свойство с указанным именем.  
  
## Синтаксис  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## Параметры  
 `object`  
 Обязательное.  Экземпляр объекта.  
  
 `proName`  
 Обязательное.  Строковое значение имени свойства.  
  
## Заметки  
 Метод `hasOwnProperty` возвращает значение `true`, если объект `object` имеет свойство с указанным именем, и значение `false` в противном случае.  Данный метод не проверяет свойства в цепочке прототипов объекта; свойство должно быть членом самого объекта.  
  
 Это свойство не поддерживается для объектов узла для Internet Explorer 8 и ниже.  
  
## Пример  
 В следующем примере все объекты `String` используют общий метод split.  Следующий код выводит значение **false** и **true**.  
  
```javascript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## См. также  
 [Оператор in](../../javascript/reference/in-operator-decrementjavascript.md)