---
title: "Метод subarray (Uint8Array) | Microsoft Docs"
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
ms.assetid: 07724c80-5fdf-4745-a750-214630100439
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Метод subarray (Uint8Array)
Получает новое представление Uint8Array хранилища [Объект ArrayBuffer](../../javascript/reference/arraybuffer-object.md) для этого массива, указывая первый и последний член подмассива.  
  
## Синтаксис  
  
```javascript  
var newUint8Array = uint8Array.subarray(begin, end);  
```  
  
## Параметры  
 `newUint8Array`  
 Подмассив, возвращаемый данным методом.  
  
 `begin`  
 Начальный индекс массива.  
  
 `end`  
 Конечный индекс массива.  Элемента с таким индексом нет в массиве.  
  
## Заметки  
 Если параметр `begin` или `end` имеет отрицательное значение, он ссылается на индекс, считая с конца массива, а не с начала.  Если параметр `end` не указан, подмассив содержит все элементы, начиная с `begin` и до конца типизированного массива.  Диапазон, заданный значениями `begin` и `end`, ограничен допустимым диапазоном индексов текущего массива.  Если вычисленная длина нового типизированного массива отрицательна, ей присваивается значение ноль.  Возвращаемый массив имеет тот же тип, что и массив, для которого был вызван этот метод.  
  
## Пример  
 В следующем примере показано, как получить подмассив из двух элементов, начиная с первого элемента массива.  
  
```javascript  
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
  
## Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]