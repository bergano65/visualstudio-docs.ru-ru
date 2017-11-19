---
title: "Свойство Length (массив) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Array object
- Length property
- length property (array)
ms.assetid: e1c6377c-2e84-440a-9660-f1f512e4a938
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e69fd5387b1d7430491b1693dec07581f165cc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-array-javascript"></a>Свойство length (массив) (JavaScript)
Получает или задает длину массива. Представляет собой число, на единицу превышающее индекс последнего определенного элемента массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
numVar = arrayObj.length   
```  
  
## <a name="parameters"></a>Параметры  
 `numVar`  
 Обязательный. Любое число.  
  
 `arrayObj`  
 Обязательный. Любой объект `Array`.  
  
## <a name="remarks"></a>Примечания  
 Массивы JavaScript являются разреженными, а элементы в них не обязательно должны следовать подряд. Свойство `length` не обязательно совпадает с числом элементов массива. Например, в следующем определении массива свойство `my_array.length` содержит значение 7, а не 2:  
  
```JavaScript  
var my_array = new Array( );  
my_array[0] = "Test";  
my_array[6] = "Another Test";  
```  
  
 Если свойство `length` получает значение, меньшее его предыдущего значения, массив усекается, а все элементы, индексы которых равны или больше нового значения свойства `length`, теряются.  
  
 Если свойство length получает значение, большее его предыдущего значения, массив расширяется, а все новые созданные элементы имеют значение `undefined`.  
  
 В следующем примере показано применение свойства `length`.  
  
```JavaScript  
var a;  
a = new Array(0,1,2,3,4);  
document.write(a.length);  
  
// Output  
// 5  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
> [!NOTE]
>  Начиная с Internet Explorer 9 (стандартный режим), конечные запятые, включаемые в инициализацию массива, обрабатываются иначе.