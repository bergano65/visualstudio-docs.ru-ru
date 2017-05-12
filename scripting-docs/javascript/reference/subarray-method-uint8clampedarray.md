---
title: "Метод subarray (Uint8ClampedArray) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 309ed9e8-5805-47ab-b3ed-501cae1323dd
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Метод subarray (Uint8ClampedArray)
Возвращает новое представление [Uint8ClampedArray](../../javascript/reference/uint8array-object.md) хранилища [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) для этого массива, используя первый и последний члены подмассива.  
  
## Синтаксис  
  
```javascript  
var newUint8ClampedArray = uint8ClampedArray.subarray(begin, end);  
```  
  
## Параметры  
 `newUint8ClampedArray`  
 Обязательный.  Подмассив, возвращаемый данным методом.  
  
 `begin`  
 Необязательно.  Начальный индекс массива.  
  
 `end`  
 Необязательно.  Конечный индекс массива.  Элемента с таким индексом нет в массиве.  
  
## Заметки  
 Если параметр `begin` или `end` имеет отрицательное значение, он ссылается на индекс, считая с конца массива, а не с начала.  Если параметр `end` не указан, подмассив содержит все элементы, начиная с `begin` и до конца типизированного массива.  Диапазон, заданный значениями `begin` и `end`, ограничен допустимым диапазоном индексов текущего массива.  Если вычисленная длина нового типизированного массива отрицательна, ей присваивается значение ноль.  Возвращаемый массив имеет тот же тип, что и массив, для которого был вызван этот метод.  
  
## Пример  
 В следующем примере показано, как получить подмассив из двух элементов, начинающийся с первого элемента массива.  
  
```javascript  
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
  
## Требования  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## См. также  
 [Объект Uint8Array](../../javascript/reference/uint8array-object.md)   
 [Объект ArrayBuffer](../../javascript/reference/arraybuffer-object.md)   
 [Объект Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)