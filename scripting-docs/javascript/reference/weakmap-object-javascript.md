---
title: "Объект WeakMap (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WeakMap
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8de97f8acb94921090696e9019a1df5d945db7c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="weakmap-object-javascript"></a>Объект WeakMap (JavaScript)
Коллекция пар «ключ-значение», в которой каждый ключ является ссылкой на объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
weakmapObj = new WeakMap()  
```  
  
## <a name="remarks"></a>Примечания  
 Объект `WeakMap` не удается перечислить объект.  
  
 При добавлении значения в коллекцию с помощью существующего ключа новое значение заменяет старое.  
  
 В `WeakMap` объект ссылки на объекты ключей удерживаются «слабо». Это означает, что `WeakMap` не будет предотвращать сборку мусора ключа объектах. При отсутствии ссылок (отличных от `WeakMap`) объектов ключей, сборщик мусора может собирать объекты ключей.  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены свойства объекта `WeakMap`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Конструктор](../../javascript/reference/constructor-property-weakmap.md)|Указывает функцию, которая создает `WeakMap`.|  
|[прототип](../../javascript/reference/prototype-property-weakmap.md)|Возвращает ссылку на прототип для `WeakMap`.|  
  
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `WeakMap`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-weakmap-javascript.md)|Удаляет все элементы из `WeakMap`.|  
|[удалить](../../javascript/reference/delete-method-weakmap-javascript.md)|Удаляет указанный элемент из `WeakMap`.|  
|[get](../../javascript/reference/get-method-weakmap-javascript.md)|Возвращает указанный элемент из `WeakMap`.|  
|[имеет](../../javascript/reference/has-method-weakmap-javascript.md)|Возвращает `true` Если `WeakMap` содержит указанный элемент.|  
|[set](../../javascript/reference/set-method-weakmap-javascript.md)|Добавляет новый элемент в `WeakMap`.|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|Возвращает строковое представление `WeakMap`.|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|Возвращает примитивное значение указанного объекта.|  
  
## <a name="example"></a>Пример  
 Следующий пример демонстрирует добавление членов в `WeakMap` объекта и затем извлечение их.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]