---
title: "Оператор instanceof (JavaScript) | Microsoft Docs"
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
  - "instanceof_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "instanceOf - оператор"
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Оператор instanceof (JavaScript)
Возвращает логическое значение, указывающее, является ли объект экземпляром определенного класса.  
  
## Синтаксис  
  
```  
  
result = object instanceof class  
```  
  
## Параметры  
 `result`  
 Обязательный.  Любая переменная.  
  
 `object`  
 Обязательный.  Любое выражение объекта.  
  
 `class`  
 Обязательный.  Любой определенный класс объектов.  
  
## Заметки  
 Оператор `instanceof` возвращает значение `true`, если объект, определяемый параметром `object`, является экземпляром класса, определяемого параметром `class`.  Он возвращает значение `true`, если класс, определяемый параметром `class`, присутствует в цепочке прототипов данного объекта.  Он возвращает значение `false`, если объект, определяемый параметром `object`, не является экземпляром класса, определяемого параметром `class`, или параметр `object` имеет значение `null`.  
  
## Пример  
 В следующем примере показано использование оператора `instanceof`.  
  
```javascript  
function objTest(obj){  
    var i, t, s = "";  
    t = new Array();  
    t["Date"] = Date;  
    t["Object"] = Object;  
    t["Array"] = Array;  
        for (i in t){  
            if (obj instanceof t[i]) {   
                s += "obj is an instance of " + i + "<br/>";  
            }  
            else {  
                s += "obj is not an instance of " + i + "<br/>";  
        }  
    }  
    return(s);  
}  
  
var obj = new Date();  
document.write(objTest(obj));  
  
// Output:   
// obj is an instance of Date  
// obj is an instance of Object  
// obj is not an instance of Array  
```  
  
## Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## См. также  
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)