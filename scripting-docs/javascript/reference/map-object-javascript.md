---
title: "Объект Map (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Map"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a91dbcbe-f58d-41a0-be15-8c9d30020327
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Объект Map (JavaScript)
Коллекция пар "ключ\-значение".  
  
## Синтаксис  
  
```javascript  
mapObj = new Map()  
```  
  
## Заметки  
 Ключи и значения в коллекции могут быть любого типа.  Если добавить значение в коллекцию с помощью существующего ключа, новое значение заменит старое значение.  
  
## Свойства  
 В следующей таблице перечислены свойства объекта `Map`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Конструктор](../../javascript/reference/constructor-property-map.md)|Указывает функцию, которая создает сопоставление.|  
|[прототип](../../javascript/reference/prototype-property-map.md)|Возвращает ссылку на прототип для сопоставления.|  
|[size](../../javascript/reference/size-property-map-javascript.md)|Возвращает число элементов в сопоставлении.|  
  
## Методы  
 В следующей таблице перечислены методы объекта `Map`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[clear](../../javascript/reference/clear-method-map-javascript.md)|Удаляет все элементы из сопоставления.|  
|[удаление](../../javascript/reference/delete-method-map-javascript.md)|Удаляет указанный элемент из сопоставления.|  
|[forEach](../../javascript/reference/foreach-method-map-javascript.md)|Выполняет указанное действие с каждым элементом в сопоставлении.|  
|[get](../../javascript/reference/get-method-map-javascript.md)|Возвращает заданный элемент из сопоставления.|  
|[не имеет](../../javascript/reference/has-method-map-javascript.md)|Возвращает значение `true`, если сопоставление содержит указанный элемент.|  
|[set](../../javascript/reference/set-method-map-javascript.md)|Добавляет новый элемент в сопоставление.|  
|[toString](../../javascript/reference/tostring-method-map-javascript.md)|Возвращает строковое представление сопоставления.|  
|[valueOf](../../javascript/reference/valueof-method-map-javascript.md)|Возвращает примитивное значение указанного объекта.|  
  
## Пример  
 В следующем примере показано, как добавить члены в `Map` и затем извлечь один из них.  
  
```javascript  
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
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]