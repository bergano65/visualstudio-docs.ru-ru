---
title: "Метод subarray (Float32Array) | Microsoft Docs"
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
ms.assetid: 97aa27c0-d650-411e-b929-dd9c4a2ae9a5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Метод subarray (Float32Array)
Получает новое представление Float32Array хранилища [Объект ArrayBuffer](../../javascript/reference/arraybuffer-object.md) для этого массива, указывая первый и последний член подмассива.  
  
## Синтаксис  
  
```javascript  
var newFloat32Array = float32Array.subarray(begin, end);  
```  
  
## Параметры  
 `newFloat32Array`  
 Подмассив, возвращаемый данным методом.  
  
 `begin`  
 Начальный индекс массива.  
  
 `end`  
 Конечный индекс массива.  
  
## Заметки  
 Если `begin` или `end` имеет отрицательное значение, он ссылается на индекс из конца массива, иначе — из начала.  Если `end` не указано, подмассив содержит все элементы, начиная с `begin` и до конца типизированного массива.  Диапазон, заданный значениями `begin` и `end`, ограничен допустимым диапазоном индексов для текущего массива.  Если вычисленная длина нового типизированного массива отрицательна, длина примет значение равное нулю.  Возвращаемый массив является массивом того же типа, что и массив, на котором был вызван этот метод.  
  
## Пример  
 В следующем примере показано, как получить подмассив из трех элементов, начиная с первого элемента массива.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var floatArr = new Float32Array(buffer.byteLength / 4);  
            var subArr = floatArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]