---
title: "for... инструкции (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47154261fd4817ba95b8884bd6482a87e044a5a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="forof-statement-javascript"></a>Оператор for...of (JavaScript)
Выполняет один или несколько операторов для каждого значения итератора, полученного от итерируемого объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
for (variable of object) {  
    statements   
}  
```  
  
## <a name="parameters"></a>Параметры  
 `variable`  
 Обязательный. Переменная, которая может представлять значение любого свойства объекта `object`.  
  
 `object`  
 Обязательный. Итерируемый объект, такой как `Array`, `Map`, `Set`, или объект, реализующий интерфейс [интерфейсы итератора](http://msdn.microsoft.com/en-us/3692355a-a703-4d43-8fb5-c03b4b7e8db1).  
  
 `statements`  
 Необязательно. Один или несколько операторов, которые необходимо выполнять для каждого значения объекта `object`. Может быть составным оператором.  
  
## <a name="remarks"></a>Примечания  
 В начале каждой итерации цикла значение параметра `variable` имеет следующее значение свойства объекта `object`.  
  
## <a name="example"></a>Пример  
 В следующем примере показано применение оператора `for...of` к массиву.  
  
```JavaScript  
let arr = [ "fred", "tom", "bob" ];  
  
for (let i of arr) {  
    console.log(i);  
}  
  
// Output:  
// fred  
// tom  
// bob  
  
```  
  
## <a name="example"></a>Пример  
 В следующем примере показано применение оператора `for...of` к объекту `Map`.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
  
for (var n of m) {  
  console.log(n);  
}  
  
// Output:  
// 1,black  
// 2,red  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>См. также  
 [for... в инструкции](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Оператор For](../../javascript/reference/for-statement-javascript.md)   
 [Оператор while](../../javascript/reference/while-statement-javascript.md)