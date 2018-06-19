---
title: for... инструкции (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2373d319347f927304c32cb47856405a1d69a6b2
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454600"
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
 Обязательно. Переменная, которая может представлять значение любого свойства объекта `object`.  
  
 `object`  
 Обязательно. Итерируемый объект, такой как `Array`, `Map`, `Set`, или объект, реализующий интерфейс [интерфейсы итератора](../../javascript/advanced/iterators-and-generators-javascript.md).  
  
 `statements`  
 Необязательный. Один или несколько операторов, которые необходимо выполнять для каждого значения объекта `object`. Может быть составным оператором.  
  
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