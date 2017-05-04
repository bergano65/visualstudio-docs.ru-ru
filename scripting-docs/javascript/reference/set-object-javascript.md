---
title: "Объект Set (JavaScript) | Microsoft Docs"
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
  - "Set"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4a4dd749-2a76-44fb-9cb0-a3ef317f75fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Объект Set (JavaScript)
Коллекция уникальных значений, которые могут быть любого типа.  
  
## Синтаксис  
  
```  
setObj = new Set()  
  
```  
  
## Заметки  
 При добавлении неуникального значения в `Set` новое значение не будет добавлено в коллекцию.  
  
## Свойства  
 В следующей таблице перечислены свойства объекта `Set`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Конструктор](../../javascript/reference/constructor-property-set.md)|Указывает функцию, которая создает набор.|  
|[прототип](../../javascript/reference/prototype-property-set.md)|Возвращает ссылку на прототип для набора.|  
|[size](../../javascript/reference/size-property-set-javascript.md)|Возвращает число элементов в наборе.|  
  
## Методы  
 В следующей таблице перечислены методы объекта `Set`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[add](../../javascript/reference/add-method-set-javascript.md)|Добавляет элемент в набор.|  
|[clear](../../javascript/reference/clear-method-set-javascript.md)|Удаляет все элементы из набора.|  
|[удаление](../../javascript/reference/delete-method-set-javascript.md)|Удаляет указанный элемент из набора.|  
|[forEach](../../javascript/reference/foreach-method-set-javascript.md)|Выполняет указанное действие с каждым элементом в наборе.|  
|[не имеет](../../javascript/reference/has-method-set-javascript.md)|Возвращает значение `true`, если набор содержит указанный элемент.|  
|[toString](../../javascript/reference/tostring-method-set-javascript.md)|Возвращает строковое представление набора.|  
|[valueOf](../../javascript/reference/valueof-method-set-javascript.md)|Возвращает примитивное значение указанного объекта.|  
  
## Пример  
 В следующем примере показано, как добавить члены в набор и затем извлечь один из них.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]