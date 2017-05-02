---
title: "Метод subarray (Uint32Array) | Microsoft Docs"
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
ms.assetid: 4c183208-12ec-4051-bf0f-a4f7c112cea1
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Метод subarray (Uint32Array)
Возвращает новое представление Uint32Array хранилища [Объект ArrayBuffer](../../javascript/reference/arraybuffer-object.md) для этого массива, указывая первый и последний члены подмассива.  
  
## Синтаксис  
  
```javascript  
var newUint32Array = uint32Array.subarray(begin, end);  
```  
  
## Параметры  
 `newUint32Array`  
 Подмассив, возвращаемый данным методом.  
  
 `begin`  
 Начальный индекс массива.  
  
 `end`  
 Конечный индекс массива.  Элемента с таким индексом нет в массиве.  
  
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
            var intArr = new Uint32Array(buffer.byteLength / 4);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]