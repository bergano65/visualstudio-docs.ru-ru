---
title: "Метод SubArray (Uint8Array) | Документы Microsoft"
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
ms.assetid: 07724c80-5fdf-4745-a750-214630100439
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a972f2bb682c9a43a5671d457b8a1efc29d2af2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-uint8array"></a>Метод subarray (Uint8Array)
Получает новое представление Uint8Array [объект ArrayBuffer](../../javascript/reference/arraybuffer-object.md) хранения для этого массива, указывая первый и последний члены подмассива.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
var newUint8Array = uint8Array.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Параметры  
 `newUint8Array`  
 Подмассив, возвращаемый данным методом.  
  
 `begin`  
 Начальный индекс массива.  
  
 `end`  
 Конечный индекс массива. Элемента с таким индексом нет в массиве.  
  
## <a name="remarks"></a>Примечания  
 Если параметр `begin` или `end` имеет отрицательное значение, он ссылается на индекс, считая с конца массива, а не с начала. Если параметр `end` не указан, подмассив содержит все элементы, начиная с `begin` и до конца типизированного массива. Диапазон, заданный значениями `begin` и `end`, ограничен допустимым диапазоном индексов текущего массива. Если вычисленная длина нового типизированного массива отрицательна, ей присваивается значение ноль. Возвращаемый массив имеет тот же тип, что и массив, для которого был вызван этот метод.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как получить подмассив из двух элементов, начиная с первого элемента массива.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var intArr = new Uint8Array(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]