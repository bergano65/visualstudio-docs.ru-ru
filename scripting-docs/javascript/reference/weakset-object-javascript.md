---
title: "Объект WeakSet (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f97e6e7c-d678-4e32-978e-d949a7cafa3a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Объект WeakSet (JavaScript)
Коллекция уникальных объектов, которые могут принадлежать к любому типу.  
  
## Синтаксис  
  
```  
setObj = new WeakSet()  
```  
  
## Заметки  
 При добавлении неуникального объекта в `WeakSet` новый объект не будет добавлен в коллекцию.  
  
 В отличие от `Set`, в коллекцию могут быть добавлены только объекты.  Произвольные значения не могут быть добавлены в коллекцию.  
  
 В объекте `WeakSet` ссылки на объекты в наборе удерживаются "слабо".  Это означает, что `WeakSet` не будет предотвращать сборку мусора в объектах.  При отсутствии ссылок \(отличных от `WeakSet`\) на объекты сборщик мусора может собирать объекты.  
  
 `WeakSet` \(или `WeakMap`\) может оказаться полезным в некоторых сценариях, где применяется кэширование объектов или метаданных объекта.  Например, метаданные для нерасширяемых объектов могут храниться в `WeakSet` или вы можете создать кэш изображений пользователя с помощью `WeakSet`.  
  
## Свойства  
 В следующей таблице перечислены свойства объекта `WeakSet`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|constructor|Указывает функцию, которая создает набор.|  
|prototype|Возвращает ссылку на прототип для набора.|  
  
## Методы  
 В следующей таблице перечислены методы объекта `WeakSet`.  
  
|Метод|Описание|  
|-----------|--------------|  
|add|Добавляет элемент в набор.|  
|delete|Удаляет указанный элемент из набора.|  
|has|Возвращает `true`, если набор содержит указанный элемент.|  
  
## Пример  
 В следующем примере показано, как добавить элементы в набор, а затем проверить, что они были добавлены.  
  
```javascript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]