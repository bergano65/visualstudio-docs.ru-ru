---
title: "Метод SubArray (Float64Array) | Документы Microsoft"
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
ms.assetid: f3c24e1b-5fb2-49a1-8183-0fda33dbeaba
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08f72854b9dc87394bdce2552d5d48ff4b1270f8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-float64array"></a>Метод subarray (Float64Array)
Получает новое представление Float64Array [объект ArrayBuffer](../../javascript/reference/arraybuffer-object.md) хранения для этого массива, указывая первый и последний члены подмассива.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
var newFloat64Array = float64Array.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Параметры  
 `newFloat64Array`  
 Подмассив, возвращаемый данным методом.  
  
 `begin`  
 Начальный индекс массива.  
  
 `end`  
 Конечный индекс массива.  
  
## <a name="remarks"></a>Примечания  
 Если параметр `begin` или `end` имеет отрицательное значение, он ссылается на индекс, считая с конца массива, а не с начала. Если параметр `end` не указан, подмассив содержит все элементы, начиная с `begin` и до конца типизированного массива. Диапазон, заданный значениями `begin` и `end`, ограничен допустимым диапазоном индексов текущего массива. Если вычисленная длина нового типизированного массива отрицательна, ей присваивается значение ноль. Возвращаемый массив имеет тот же тип, что и массив, для которого был вызван этот метод.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как получить подмассив из трех элементов, начинающийся с первого элемента массива.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var floatArr = new Float64Array(buffer.byteLength / 8);  
            var subArr = floatArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]