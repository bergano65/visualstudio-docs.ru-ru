---
title: "Объект WeakMap (JavaScript) | Microsoft Docs"
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
  - "WeakMap"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Объект WeakMap (JavaScript)
Коллекция пар "ключ\-значение", в каждой из которых ключ — это ссылка на объект.  
  
## Синтаксис  
  
```  
weakmapObj = new WeakMap()  
```  
  
## Заметки  
 Объект `WeakMap` не может быть перечислен.  
  
 Если добавить значение в коллекцию с помощью существующего ключа, новое значение заменит старое значение.  
  
 В объекте `WeakMap` ссылки на ключевые объекты удерживаются "слабо".  Это означает, что `WeakMap` не останавливает сборку мусора на ключевых объектах.  Если нет ссылки \(кроме `WeakMap`\) к ключевым объектам, сборщик мусора может собрать объекты раздела.  
  
## Свойства  
 В следующей таблице перечислены свойства объекта `WeakMap`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Конструктор](../../javascript/reference/constructor-property-weakmap.md)|Указывает функцию, которая создает `WeakMap`.|  
|[прототип](../../javascript/reference/prototype-property-weakmap.md)|Возвращает ссылку на прототип для `WeakMap`.|  
  
## Методы  
 В следующей таблице перечислены методы объекта `WeakMap`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[clear](../../javascript/reference/clear-method-weakmap-javascript.md)|Удаляет все элементы из `WeakMap`.|  
|[удаление](../../javascript/reference/delete-method-weakmap-javascript.md)|Удаляет указанный элемент из `WeakMap`.|  
|[get](../../javascript/reference/get-method-weakmap-javascript.md)|Возвращает указанный элемент из `WeakMap`.|  
|[не имеет](../../javascript/reference/has-method-weakmap-javascript.md)|Возвращает значение `true`, если `WeakMap` содержит указанный элемент.|  
|[set](../../javascript/reference/set-method-weakmap-javascript.md)|Добавляет новый элемент в `WeakMap`.|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|Возвращает строковое представление `WeakMap`.|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|Возвращает примитивное значение указанного объекта.|  
  
## Пример  
 В следующем примере показано, как добавить члены в объект `WeakMap` и затем извлечь один из них.  
  
```javascript  
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
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]