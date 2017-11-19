---
title: "Объект Map (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Map
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a91dbcbe-f58d-41a0-be15-8c9d30020327
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d89890f9fecaf61e47e136734ed7fefb7b73cabd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="map-object-javascript"></a>Объект Map (JavaScript)
Коллекция пар «ключ-значение».  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
mapObj = new Map()  
```  
  
## <a name="remarks"></a>Примечания  
 Ключи и значения в коллекции может быть любого типа. При добавлении значения в коллекцию с помощью существующего ключа новое значение заменяет старое.  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены свойства объекта `Map`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Конструктор](../../javascript/reference/constructor-property-map.md)|Указывает функцию, которая создает карту.|  
|[прототип](../../javascript/reference/prototype-property-map.md)|Возвращает ссылку на прототип для карты.|  
|[size](../../javascript/reference/size-property-map-javascript.md)|Возвращает количество элементов в сопоставлении.|  
  
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `Map`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-map-javascript.md)|Удаляет все элементы из карты.|  
|[удалить](../../javascript/reference/delete-method-map-javascript.md)|Удаляет указанный элемент из сопоставления.|  
|[по каждому элементу](../../javascript/reference/foreach-method-map-javascript.md)|Выполняет указанное действие для каждого элемента на карте.|  
|[get](../../javascript/reference/get-method-map-javascript.md)|Возвращает указанный элемент из сопоставления.|  
|[имеет](../../javascript/reference/has-method-map-javascript.md)|Возвращает `true` Если сопоставление содержит указанный элемент.|  
|[set](../../javascript/reference/set-method-map-javascript.md)|Добавляет новый элемент в сопоставление.|  
|[toString](../../javascript/reference/tostring-method-map-javascript.md)|Возвращает строковое представление карты.|  
|[valueOf](../../javascript/reference/valueof-method-map-javascript.md)|Возвращает примитивное значение указанного объекта.|  
  
## <a name="example"></a>Пример  
 В следующем примере показано добавление членов в объект `Map` и затем извлечение их.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]