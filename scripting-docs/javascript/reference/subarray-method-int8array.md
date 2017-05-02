---
title: "Метод subarray (Int8Array) | Microsoft Docs"
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
ms.assetid: 46271ed6-a3c3-41fb-bd6f-81efa9e8dedc
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Метод subarray (Int8Array)
Получает новое представление Int8Array хранилища ArrayBuffer для этого массива, ссылаясь на элементы с индекса begin \(включая элемент с этим индексом\) до индекса end \(исключая элемент с этим индексом\).  
  
## Синтаксис  
  
```javascript  
var newInt8Array = int8Array.subset(begin, end);  
```  
  
## Параметры  
 `newInt8Array`  
 Подмассив, возвращаемый данным методом.  
  
 `begin`  
 Начальный индекс массива.  
  
 `end`  
 Конечный индекс массива.  Элемента с таким индексом нет в массиве.  
  
## Заметки  
 Если параметр begin или end имеет отрицательное значение, он ссылается на индекс, считая с конца массива, а не с начала.  Если параметр end не задан, подмассив содержит все элементы с начала и до конца массива TypedArray.  Диапазон, заданный значениями begin и end, ограничен допустимым диапазоном индексов текущего массива.  Если вычисленная длина нового массива TypedArray отрицательна, ей присваивается значение ноль.  Возвращаемый массив TypedArray имеет тот же тип, что и массив, для которого был вызван этот метод.  
  
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
            var dataView = new DataView(buffer);  
            var intArr = new Int8Array(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]