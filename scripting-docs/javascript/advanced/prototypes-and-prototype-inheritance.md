---
title: "Прототипы и наследование прототипов | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- prototype [JavaScript]
- prototype inheritance [JavaScript]
ms.assetid: 1e1d0631-2a9f-4011-b9fe-fa338e1ef34c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 3fb5627d2cc92c36e9dcf34f4b94796b6620321f
ms.openlocfilehash: ade60bcbbfad166bae18b650daa6906f9983d4cd
ms.contentlocale: ru-ru
ms.lasthandoff: 08/11/2017

---
# <a name="prototypes-and-prototype-inheritance"></a>Прототипы и наследование прототипов
В JavaScript `prototype` — это свойство функций и объектов, создаваемых функциями конструктора. Прототипом функции является объект. В основном он применяется тогда, когда функция используется в качестве конструктора.  
  
```JavaScript  
function Vehicle(wheels, engine) {  
    this.wheels = wheels;  
    this.engine = engine;  
}  
```  
  
 В приведенном выше примере прототип функции `Vehicle` является прототипом любого объекта, экземпляр которого создается с помощью конструктора `Vehicle`.  
  
## <a name="using-prototypes-to-add-properties-and-methods"></a>Использование прототипов для добавления свойств и методов  
 Свойство `prototype` можно использовать для добавления свойств и методов в объекты — даже в те, которые уже созданы:  
  
```JavaScript  
var testVehicle = new Vehicle(2, false);  
Vehicle.prototype.color = "red";  
var testColor = testVehicle.color;  
```  
  
 Значение переменной `testColor` — red.  
  
 Добавлять свойства и методы можно даже в предопределенные объекты. Например, можно определить метод `Trim` в объекте-прототипе `String`, и все строки будут скрипта наследовать этот метод.  
  
```JavaScript  
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
  
### <a name="using-prototypes-to-derive-one-object-from-another-with-objectcreate"></a>Использование прототипов для наследования одного объекта от другого с помощью Object.create  

Прототип `Object` можно использовать для наследования одного объекта от другого. Например, можно использовать функцию [Object.create](../../javascript/reference/object-create-function-javascript.md) для наследования нового объекта `Bicycle` на основе ранее определенного прототипа объекта `Vehicle` (а также каких-либо новых необходимых свойств).  
  
```JavaScript  
var bicycle = Object.create(Object.getPrototypeOf(Vehicle), {  
    "pedals" :{value: true}  
});  
  
```  
  
 Объект `bicycle` имеет свойства `wheels`, `engine`, `color` и `pedals`, и его прототипом является `Vehicle.prototype`. Обработчик скриптов JavaScript находит свойство `pedals` в объекте `bicycle` и просматривает цепочку прототипов, чтобы найти свойства `wheels`, `engine` и `color` в объекте `Vehicle`.  
  
### <a name="changing-an-objects-prototype"></a>Изменение прототипа объекта  
 В Internet Explorer 11 внутренний прототип объекта или функции можно заменить новым прототипом с помощью свойства [__proto\_\_](../../javascript/reference/proto-property-object-javascript.md). При использовании этого свойства наследуются свойства и методы нового прототипа вместе с другими свойствами и методами в его цепочке прототипов.  
  
 В следующем примере показано изменение прототипа объекта. В нем демонстрируется изменение наследуемых свойств объекта при изменении его прототипа.  
  
```JavaScript  
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

