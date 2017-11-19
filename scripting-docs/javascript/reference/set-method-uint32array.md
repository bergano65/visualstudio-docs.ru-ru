---
title: "Метод set (Uint32Array) | Документы Microsoft"
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
ms.assetid: 00f521b2-db27-45ec-bdee-2891983618b9
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c28d4b8415ef9bab56e3aa0937b051ceb6989f75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="set-method-uint32array"></a>Метод set (Uint32Array)
Задает значение или массив значений.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
uint32Array.set(index, value);  
uint32Array.set(array, offset);  
  
```  
  
## <a name="parameters"></a>Параметры  
 `index`  
 Индекс задаваемого расположения.  
  
 `value`  
 Задаваемое значение.  
  
 `array`  
 Типизированный или нетипизированный массив задаваемых значений.  
  
 `offset`  
 Индекс в текущем массиве, начиная с которого должны быть записаны значения.  
  
## <a name="remarks"></a>Примечания  
 Если входной массив является массивом TypedArray, для обоих массивов может использоваться один и тот же базовый буфер ArrayBuffer. В этой ситуации задание значений происходит так, как если бы все данные сначала копировались во временный буфер, не перекрывающийся ни с одним из массивов, а затем данные из временного буфера копировались бы в текущий массив.  
  
 Если смещение плюс длина заданного массива находятся вне диапазона текущего массива TypedArray, вызывается исключение.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как задать первый элемент массива.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint32Array(buffer.byteLength / 4);  
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]