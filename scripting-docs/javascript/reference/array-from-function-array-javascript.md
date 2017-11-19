---
title: "Функция Array.From (Array) (JavaScript) | Документы Microsoft"
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
ms.assetid: 1bf59a99-f860-4c4d-b4c6-d5f1f946a490
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a240cb439942bfeb6b4c9a1febb4d24cef1c5c18
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="arrayfrom-function-array-javascript"></a>Функция Array.from (Array) (JavaScript)
Возвращает массив из итерируемого объекта или объекта, имеющего вид массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Array.from (arrayLike [ , mapfn [ , thisArg ] ] );  
```  
  
#### <a name="parameters"></a>Параметры  
 `arrayLike`  
 Обязательный. Итерируемый объект или объект, имеющий вид массива.  
  
 `mapfn`  
 Необязательно. Функция сопоставления, которую необходимо вызвать для каждого элемента в `arrayLike`.  
  
 `thisArg`  
 Необязательно. Определяет объект `this` в функции сопоставления.  
  
## <a name="remarks"></a>Примечания  
 Параметр `arrayLike` должен быть либо объектом с индексированными элементами и свойством `length`, либо итерируемым объектом, таким как объект `Set`.  
  
 Необязательная функция сопоставления вызывается для каждого элемента в массиве.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается массив из коллекции узлов элементов DOM.  
  
```JavaScript  
var elemArr = Array.from(document.querySelectorAll('*'));  
var elem = elemArr[0]; // elem contains a reference to the first DOM element  
  
```  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается массив символов.  
  
```JavaScript  
var charArr = Array.from("abc");  
// charArr[0] == "a";  
```  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается массив объектов, содержащихся в коллекции.  
  
```JavaScript  
var setObj = new Set("a", "b", "c");  
var objArr = Array.from(setObj);  
// objArr[1] == "b";   
```  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как изменять значение элементов, используя синтаксис стрелок и функцию сопоставления.  
  
```JavaScript  
var arr = Array.from([1, 2, 3], x => x * 10);  
// arr[0] == 10;  
// arr[1] == 20;  
// arr[2] == 30;  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]