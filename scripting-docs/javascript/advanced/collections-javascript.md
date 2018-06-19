---
title: Коллекции (JavaScript) | Документы Майкрософт
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
ms.assetid: 23c26185-6a7b-4b69-9d22-63e1841b4905
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fab554f50f6d2fcdac92c562333e625dc0eb32f6
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2018
ms.locfileid: "27783056"
---
# <a name="collections-javascript"></a>Коллекции (JavaScript)
Для хранения значений и объектов можно использовать объекты коллекции [Map](../../javascript/reference/map-object-javascript.md), [Set](../../javascript/reference/set-object-javascript.md) и [WeakMap](../../javascript/reference/weakmap-object-javascript.md). Эти объекты предоставляют удобные методы для добавления и извлечения членов с помощью ключа или значения вместо индекса. Для доступа к элементам коллекции с помощью индекса используйте объект `Array`. Дополнительные сведения см. в разделе [Использование массивов](../../javascript/advanced/using-arrays-javascript.md).  
  
> [!CAUTION]
>  В версиях браузера до Internet Explorer 11 объекты `Map`, `Set` и `WeakMap` не поддерживаются. Дополнительные сведения о поддержке версий см. в разделе [Сведения о версии](../../javascript/reference/javascript-version-information.md).  
  
## <a name="using-collections"></a>Использование коллекций  
 В объектах `Map` и `WeakMap` хранятся пары "ключ-значение" и эти объекты позволяют добавлять, извлекать и удалять члены с помощью ключа. Ключ и значение могут быть любого типа. В объекте `Set` хранятся значения любого типа.  
  
 Объекты `Map` и `Set` позволяют перечислять элементы коллекции с помощью метода `forEach` и проверять размер коллекции с помощью метода `size`. Объект `WeakMap` не является перечислимым. Для этой коллекции ключевые ссылки удерживаются слабо. Если требуется, чтобы сборщик мусора определял, должно ли приложение сохранять все члены коллекции в памяти, следует использовать объект `WeakMap`. Например, это может быть полезно в сценариях кэширования, где кэшированные объекты очень большие и без необходимости их не нужно удерживать в памяти. В некоторых сценариях этот объект можно использовать для предотвращения утечек памяти.  
  
 В следующем примере показано использование объекта `Map`. В этом примере выполняется обращение к членам с помощью `get` и `forEach`. Функция обратного вызова в `forEach` может принимать до трех параметров, предоставляющих значение текущего элемента коллекции, ключа текущего элемента и самого объекта коллекции.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
document.write(m.get(2));  
document.write("<br />");  
  
m.forEach(function (value, key, mapObj) {  
    document.write(value.toString() + "<br />");  
});  
  
// Output:  
// red  
  
// black  
// red  
// 2  
// 3  
  
```  
  
 Использование объекта `WeakMap` аналогично использованию объекта `Map`, за исключением того, что члены можно извлекать только с помощью `get`. Например, см. объект [WeakMap](../../javascript/reference/weakmap-object-javascript.md).  
  
 В следующем примере показано использование объекта `Set`. В этом примере функция обратного вызова принимает один параметр, представляющий значение текущего элемента коллекции.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (value) {  
    document.write(value.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенный язык JavaScript](../../javascript/advanced/advanced-javascript.md)