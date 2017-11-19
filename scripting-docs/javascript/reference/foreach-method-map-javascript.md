---
title: "Метод forEach (Map) (JavaScript) | Документы Microsoft"
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
ms.assetid: 9cdf0adc-77c7-4407-8ba7-ada0fb09e507
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d0ffa12b9a1995df14f4868872238cdc45b674a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="foreach-method-map-javascript"></a>Метод forEach (Map) (JavaScript)
Выполняет указанное действие для каждого элемента на карте.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
mapObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Параметры  
 `mapObj`  
 Обязательный. Объект `Map`.  
  
 `callbackfn`  
 Обязательный. Функция, `forEach` вызывает один раз для каждого элемента в схеме. `callbackfn`принимает до 3 аргументов. `forEach`вызовы `callbackfn` функцию один раз для каждого элемента в сопоставлении.  
  
 `thisArg`  
 Необязательно. Объект, `this` может ссылаться ключевое слово, чтобы в `callbackfn` функции. Если параметр `thisArg` опущен, в качестве значения `undefined` используется `this`.  
  
## <a name="exceptions"></a>Исключения  
 Если аргумент `callbackfn` не является объектом функции, вызывается исключение `TypeError`.  
  
## <a name="remarks"></a>Примечания  
 Синтаксис функции обратного вызова выглядит следующим образом:  
  
 `function callbackfn(value, key, mapObj)`  
  
 Можно объявить функцию обратного вызова можно использовать до трех параметров, как показано в следующей таблице.  
  
|Аргумент обратного вызова|Определение|  
|-----------------------|----------------|  
|`value`|Значение, содержащееся в схеме.|  
|`key`|Ключ, содержащихся в схеме.|  
|`mapObj`|`Map` Объекта для обхода.|  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как для получения членов `Map` с помощью `forEach`.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]