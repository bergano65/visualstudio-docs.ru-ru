---
title: "Прототипы и их наследование | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "прототип [JavaScript]"
  - "наследование прототипов [JavaScript]"
ms.assetid: 1e1d0631-2a9f-4011-b9fe-fa338e1ef34c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Прототипы и их наследование
В JavaScript `prototype` — это свойство функций и объектов, создаваемых функциями конструктора.  Прототипом функции является объект.  В основном он применяется тогда, когда функция используется в качестве конструктора.  
  
```javascript  
function Vehicle(wheels, engine) {  
    this.wheels = wheels;  
    this.engine = engine;  
}  
```  
  
 В приведенном выше примере прототип функции `Vehicle` является прототипом любого объекта, экземпляр которого создается с помощью конструктора `Vehicle`.  
  
## Использование прототипов для добавления свойств и методов  
 Свойство `prototype` можно использовать для добавления свойств и методов в объекты — даже в те, которые уже созданы:  
  
```javascript  
var testVehicle = new Vehicle(2, false);  
Vehicle.prototype.color = "red";  
var testColor = testVehicle.color;  
```  
  
 Значение переменной `testColor` — red.  
  
 Добавлять свойства и методы можно даже в предопределенные объекты.  Например, можно определить метод `Trim` в объекте\-прототипе `String`, и все строки будут скрипта наследовать этот метод.  
  
```javascript  
String.prototype.trim = function()  
{  
    // Replace leading and trailing spaces with the empty string  
    return this.replace(/(^\s*)|(\s*$)/g, "");  
}  
var s = "    leading and trailing spaces    ";  
// Displays "    leading and trailing spaces     (35)"  
window.alert(s + " (" + s.length + ")");  
// Remove the leading and trailing spaces  
s = s.trim();  
// Displays "leading and trailing spaces (27)"  
window.alert(s + " (" + s.length + ")");  
```  
  
### Использование прототипов для наследования одного объекта от другого с помощью Object.create  
 Объект `prototype` можно использовать для наследования одного объекта от другого.  Например, можно использовать функцию [Object.create](../../javascript/reference/object-create-function-javascript.md) для наследования нового объекта `Bicycle` на основе ранее определенного прототипа объекта `Vehicle` \(а также каких\-либо новых необходимых свойств\).  
  
```javascript  
var Bicycle = Object.create(Object.getPrototypeOf(Vehicle), {  
    "pedals" :{value: true}  
});  
  
```  
  
 Объект `Bicycle` имеет свойства `wheels`, `engine`, `color` и `pedals`, и его прототипом является `Vehicle.prototype`.  Обработчик скриптов JavaScript находит свойство `pedals` в объекте `Bicycle` и просматривает цепочку прототипов, чтобы найти свойства `wheels`, `engine` и `color` в объекте `Vehicle`.  
  
### Изменение прототипа объекта  
 В Internet Explorer 11 внутренний прототип объекта или функции можно заменить новым прототипом с помощью свойства [\_\_proto](../../javascript/reference/proto-property-object-javascript.md).  При использовании этого свойства наследуются свойства и методы нового прототипа вместе с другими свойствами и методами в его цепочке прототипов.  
  
 В следующем примере показано изменение прототипа объекта.  В нем демонстрируется изменение наследуемых свойств объекта при изменении его прототипа.  
  
```javascript  
function Friend() {  
    this.demeanor = "happy";  
}  
  
function Foe() {  
    this.demeanor = "suspicious";  
}  
  
var friend = new Friend();  
var foe = new Foe();  
  
var player = new Object();  
player.__proto__ = foe;  
  
friend.ally = "Tom";  
  
if (console && console.log) {  
    console.log(player.demeanor === "happy" );      // Returns false  
    console.log(player.demeanor === "suspicious");  // Returns true  
    console.log(player.ally === "Tom");             // Returns false  
    // Turn the foe to a friend.  
    player.__proto__ = friend;  
    console.log(player.demeanor === "happy");       // Returns true  
    console.log(player.demeanor === "suspicious");  // Returns false  
    console.log(player.ally === "Tom");             // Returns true  
}  
```