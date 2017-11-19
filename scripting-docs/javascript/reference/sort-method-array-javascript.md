---
title: "Метод Sort (Array) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: sort
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Sort method
ms.assetid: 9bd8b54a-c838-4806-85c8-62eebe6bc48c
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d098b47591ca7bbb4e3e8da5e5c14f8c0e9b255
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="sort-method-array-javascript"></a>Метод sort (Array) (JavaScript)
Сортирует `Array`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## <a name="parameters"></a>Параметры  
 `arrayObj`  
 Обязательный. Любой объект `Array`.  
  
 `sortFunction`  
 Необязательно. Имя функции, используемый для определения порядка элементов. Если не указан, элементы сортируются в восходящем порядке символов ASCII.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Отсортированный массив.  
  
## <a name="remarks"></a>Примечания  
 `sort` Метод сортировки `Array` объекта на месте; нет новых `Array` объект создается во время выполнения.  
  
 Если указать функцию в `sortFunction` аргумент, оно должно возвращать одно из следующих значений:  
  
-   Отрицательное значение, если первый переданный аргумент меньше второго аргумента.  
  
-   Нуль, если аргументы эквивалентны.  
  
-   Положительное значение, если первый аргумент больше значения второго аргумента.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать метод `sort`.  
  
```JavaScript  
var a = new Array(4, 11, 2, 10, 3, 1);  
  
var b = a.sort();  
document.write(b);  
document.write("<br/>");  
  
// This is ASCII character order.  
// Output: 1,10,11,2,3,4)  
  
// Sort the array elements with a function that compares array elements.  
b = a.sort(CompareForSort);  
document.write(b);  
document.write("<br/>");  
// Output: 1,2,3,4,10,11.  
  
// Sorts array elements in ascending order numerically.  
function CompareForSort(first, second)  
{  
    if (first == second)  
        return 0;  
    if (first < second)  
        return -1;  
    else  
        return 1;   
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]