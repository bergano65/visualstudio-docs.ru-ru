---
title: Типизированные массивы (JavaScript) | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: fa82c562-0ebf-4559-aecc-166e59f7fb64
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5fc3b29a4593e7c627a6e606242229e87fa5be54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569364"
---
# <a name="typed-arrays-javascript"></a>Типизированные массивы (JavaScript)
Типизированные массивы можно использовать для обработки двоичных данных из таких источников, как сетевые протоколы, двоичные форматы файлов и буферы необработанной графики. Кроме того, типизированные массивы позволяют управлять двоичными данными в памяти с определенными байтовыми макетами.  
  
## <a name="example"></a>Пример  
 Следующий пример кода показывает, как использовать [объект ArrayBuffer](../../javascript/reference/arraybuffer-object.md) в качестве отклика [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx). Байты в отклике можно обрабатывать с помощью различных методов [объекта DataView](../../javascript/reference/dataview-object.md), а также путем копирования байтов в соответствующий типизированный массив.  
  
> [!TIP]
>  Дополнительные сведения об использовании различных типов откликов с `XmlHttpRequest` см. в статьях [XMLHttpRequest.responseType](http://msdn.microsoft.com/en-us/8d7738d1-4bfd-4cf1-8015-174def089556), [Улучшения объекта XMLHttpRequest](http://msdn.microsoft.com/en-us/be09137c-6546-441b-b953-dcbf72b77069) и [Скачивание различных типов содержимого (приложения для магазина Windows)](http://msdn.microsoft.com/en-us/c0006bbd-17f9-4c6a-af81-2acaf109111d).  
  
```JavaScript  
...  
<div id="xhrDiv"></div>  
...  
var name = "http://www.microsoft.com";  
var xhrDiv = document.getElementById("xhrDiv");  
  
var req = new XMLHttpRequest();  
req.open("GET", name, true);  
req.responseType = "arraybuffer";  
req.onreadystatechange = function () {  
if (req.readyState == req.DONE) {  
    var arrayResponse = req.response;  
    var dataView = new DataView(arrayResponse);  
    var ints = new Uint32Array(dataView.byteLength / 4);  
  
    xhrDiv.style.backgroundColor = "#00FF00";  
    xhrDiv.innerText = "Array is " + ints.length + "uints long";  
    }  
}  
req.send();  
```  
  
## <a name="arraybuffer"></a>ArrayBuffer  
 [Объект ArrayBuffer](../../javascript/reference/arraybuffer-object.md) представляет собой буфер необработанных данных, в котором хранятся данные для разных типизированных массивов. `ArrayBuffer` недоступен для чтения или записи, вы можете передать его в типизированный массив или [объект DataView](../../javascript/reference/dataview-object.md) для интерпретации необработанного буфера. `ArrayBuffer` можно использовать для хранения любого рода данных (или смешанных типов данных).  
  
## <a name="dataview"></a>DataView  
 [Объект DataView](../../javascript/reference/dataview-object.md) можно использовать для чтения и записи различных типов двоичных данных в любое место `ArrayBuffer`.  
  
## <a name="typed-arrays"></a>Типизированные массивы  
 Типы типизированных массивов — это представления [объекта ArrayBuffer](../../javascript/reference/arraybuffer-object.md), которые можно индексировать и с которыми можно выполнять различные операции. Все типы массивов имеют фиксированную длину.  
  
||||  
|-|-|-|  
|Имя|Размер (в байтах)|Описание|  
|[Объект Int8Array](../../javascript/reference/int8array-object.md)|1|8-разрядное целое число со знаком — дополнение до двух|  
|[Объект Uint8Array](../../javascript/reference/uint8array-object.md)|1|8-разрядное целое число без знака|  
|[Объект Int16Array](../../javascript/reference/int16array-object.md)|2|16-разрядное целое число со знаком — дополнение до двух|  
|[Объект Uint16Array](../../javascript/reference/uint16array-object.md)|2|16-разрядное целое число без знака|  
|[Объект Int32Array](../../javascript/reference/int32array-object.md)|4|32-разрядное целое число со знаком — дополнение до двух|  
|[Объект Uint32Array](../../javascript/reference/uint32array-object.md)|4|32-разрядное целое число без знака|  
|[Объект Float32Array](../../javascript/reference/float32array-object.md)|4|32-разрядное число с плавающей запятой (стандарт IEEE)|  
|[Объект Float64Array](../../javascript/reference/float64array-object.md)|8|64-разрядное число с плавающей запятой (стандарт IEEE)|