---
title: "Метод SubArray (Uint8ClampedArray) | Документы Microsoft"
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
ms.assetid: 309ed9e8-5805-47ab-b3ed-501cae1323dd
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76cda8b123b02b4c19a7fd162f3bfbce4540d149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-uint8clampedarray"></a>Метод subarray (Uint8ClampedArray)
Получает новый [Uint8ClampedArray](../../javascript/reference/uint8array-object.md) представление [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) хранения для этого массива, указывая первый и последний члены подмассива.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
var newUint8ClampedArray = uint8ClampedArray.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Параметры  
 `newUint8ClampedArray`  
 Обязательный. Подмассив, возвращаемый этим методом.  
  
 `begin`  
 Необязательный. Индекс начала массива.  
  
 `end`  
 Необязательный. Конечный индекс массива. Элемента с таким индексом нет в массиве.  
  
## <a name="remarks"></a>Примечания  
 Если параметр `begin` или `end` имеет отрицательное значение, он ссылается на индекс, считая с конца массива, а не с начала. Если параметр `end` не указан, подмассив содержит все элементы, начиная с `begin` и до конца типизированного массива. Диапазон, заданный значениями `begin` и `end`, ограничен допустимым диапазоном индексов текущего массива. Если вычисленная длина нового типизированного массива отрицательна, ей присваивается значение ноль. Возвращаемый массив имеет тот же тип, что и массив, для которого был вызван этот метод.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как получить подмассив из двух элементов, начинающийся с первого элемента массива.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Объект Uint8Array](../../javascript/reference/uint8array-object.md)   
 [Объект ArrayBuffer](../../javascript/reference/arraybuffer-object.md)   
 [Объект Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)