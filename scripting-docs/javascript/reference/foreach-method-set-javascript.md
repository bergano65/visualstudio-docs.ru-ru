---
title: "Метод forEach (Set) (JavaScript) | Документы Microsoft"
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
ms.assetid: 813bff6e-6098-4260-ab6e-b0d2da6be94d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b89c56b54fd74c25c43a84f2f0fd68922aa9f637
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="foreach-method-set-javascript"></a>Метод forEach (Set) (JavaScript)
Выполняет указанное действие для каждого элемента в наборе.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
setObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Параметры  
 `setObj`  
 Обязательный. Объект `Set`.  
  
 `callbackfn`  
 Обязательный. `callbackfn`принимает до 3 аргументов. Функция, `forEach` вызывает один раз для каждого элемента в наборе.  
  
 `thisArg`  
 Необязательно. Объект, `this` может ссылаться ключевое слово, чтобы в `callbackfn` функции. Если параметр `thisArg` опущен, в качестве значения `undefined` используется `this`.  
  
## <a name="exceptions"></a>Исключения  
 Если аргумент `callbackfn` не является объектом функции, вызывается исключение `TypeError`.  
  
## <a name="remarks"></a>Примечания  
 Синтаксис функции обратного вызова выглядит следующим образом:  
  
 `function callbackfn(value, key, setObj)`  
  
 Можно объявить функцию обратного вызова можно использовать до трех параметров, как показано в следующей таблице.  
  
|Аргумент обратного вызова|Определение|  
|-----------------------|----------------|  
|`value`|Значение, содержащееся в наборе.|  
|`key`|Значение, содержащееся в наборе. Набор не содержит разделы, поэтому это значение совпадает со значением `value`.|  
|`setObj`|`Set` Объекта для обхода.|  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать `forEach`. `callbackfn` Аргумент включает код функции обратного вызова.  
  
```JavaScript  
var s = new Set();  
  
s.add("scale");  
s.add(10);  
s.add("5");  
  
s.forEach(function(item, sameItem, s) {  
    document.write("Size of the set object is: " + s.size + "<br />");  
    document.write("Deleting item: " + item + "<br />");  
    s.delete(sameItem);  
});  
  
// Output:  
// Size of the set object is: 3  
// Deleting item: scale  
// Size of the set object is: 2  
// Deleting item: 10  
// Size of the set object is: 1  
// Deleting item: 5  
```  
  
## <a name="example"></a>Пример  
 Следующий пример показывает, что вы можете извлечь члены из набора, передавая только один параметр функции обратного вызова.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]