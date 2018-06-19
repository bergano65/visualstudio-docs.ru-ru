---
title: Метод Sort (Array) (JavaScript) | Документы Microsoft
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
- sort
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Sort method
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0462e60e623b99af458beb61eb7ef4215fe8ef41
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2018
ms.locfileid: "28987819"
---
# <a name="sort-method-array-javascript"></a>Метод sort (Array) (JavaScript)
Сортирует `Array`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## <a name="parameters"></a>Параметры  
 `arrayObj`  
 Обязательно. Любой объект `Array`.  
  
 `sortFunction`  
 Необязательный. Имя функции, используемый для определения порядка элементов. Если не указан, элементы сортируются в восходящем порядке символов ASCII.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Отсортированный массив.  
  
## <a name="remarks"></a>Примечания  
 `sort` Метод сортировки `Array` объекта на месте; нет новых `Array` объект создается во время выполнения.  
  
 `sortFunction`принимает два аргумента и должен возвращать одно из следующих значений:  
  
-   Отрицательное значение (меньше 0), если первый аргумент, передаваемый меньше значения второго аргумента.  Первый аргумент сортируется в нижний индекс.
  
-   Ноль (0), если два аргумента эквивалентны.  Два аргумента сортируются относительно других элементов в массиве, но не сортируются относительно друг друга.
  
-   Положительное значение (0) Если первого аргумента больше значения второго аргумента.  Нижний индекс сортируется второго аргумента.
  
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