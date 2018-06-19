---
title: Метод Push (Array) (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- push
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Push method
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddb49f310eaff51fe9e9ba584281fdf07bc2e818
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639454"
---
# <a name="push-method-array-javascript"></a>Метод push (Array) (JavaScript)
Присоединяет новые элементы к массиву и возвращает новую длину массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## <a name="parameters"></a>Параметры  
 `arrayObj`  
 Обязательный. Объект `Array`.  
  
 `item, item2,. . ., itemN`  
 Необязательно. Новые элементы `Array`.  
  
## <a name="remarks"></a>Примечания  
 `push` И `pop` методы позволяют имитировать последним поступил — первым вышел стека.  
  
 `push` Метод добавляет элементы в порядке, в котором они отображаются. Если один из аргументов является массивом, он добавляется как элемент. Используйте `concat` метод для объединения элементов из двух или более массивов.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `push`.  
  
```JavaScript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output:  
// 9 8 7 6 5  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод concat (массив)](../../javascript/reference/concat-method-array-javascript.md)   
 [Метод pop (Array)](../../javascript/reference/pop-method-array-javascript.md)