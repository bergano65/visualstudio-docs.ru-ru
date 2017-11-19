---
title: "Метод SubArray (Int8Array) | Документы Microsoft"
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
ms.assetid: 46271ed6-a3c3-41fb-bd6f-81efa9e8dedc
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e32c3a0da7e3173273eb40bf52bb6583bd77df51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-int8array"></a>Метод subarray (Int8Array)
Получает новое представление Int8Array хранилища ArrayBuffer для этого массива, ссылаясь на элементы с индекса begin (включая элемент с этим индексом) до индекса end (исключая элемент с этим индексом).  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
var newInt8Array = int8Array.subset(begin, end);  
```  
  
## <a name="parameters"></a>Параметры  
 `newInt8Array`  
 Подмассив, возвращаемый данным методом.  
  
 `begin`  
 Начальный индекс массива.  
  
 `end`  
 Конечный индекс массива. Элемента с таким индексом нет в массиве.  
  
## <a name="remarks"></a>Примечания  
 Если параметр begin или end имеет отрицательное значение, он ссылается на индекс, считая с конца массива, а не с начала. Если параметр end не задан, подмассив содержит все элементы с начала и до конца массива TypedArray. Диапазон, заданный значениями begin и end, ограничен допустимым диапазоном индексов текущего массива. Если вычисленная длина нового массива TypedArray отрицательна, ей присваивается значение ноль. Возвращаемый массив TypedArray имеет тот же тип, что и массив, для которого был вызван этот метод.  
  
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
            var dataView = new DataView(buffer);  
            var intArr = new Int8Array(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]