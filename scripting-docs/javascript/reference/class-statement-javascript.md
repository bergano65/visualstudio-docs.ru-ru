---
title: Оператор Class (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: bf45ebad-4678-4062-88df-55d32b603c69
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e828ae86c3f8f585179e3b097d98b3449c3f3b45
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634234"
---
# <a name="class-statement-javascript"></a>Оператор class (JavaScript)
Объявляет новый класс.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
class classname () [extends object] {    [constructor([arg1 [,... [,argN]]]) {        statements    }]    [[static] method([arg1 [,... [,argN]]]) {        statements    }]}  
```  
  
#### <a name="parameters"></a>Параметры  
 `classname`  
 Обязательный. Имя класса.  
  
 `object`  
 Необязательно. Объект или класс, от которого новый класс наследует свойства и методы.  
  
 `constructor`  
 Необязательно. Функция конструктора, которая инициализирует новый экземпляр класса.  
  
 `arg1...argN`  
 Необязательно. Вспомогательный список аргументов, которые понимает данная функция, разделенных запятыми.  
  
 `statements`  
 Необязательно. Один или несколько операторов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 `static`  
 Необязательно. Указывает статический метод.  
  
 `method`  
 Необязательно. Один или несколько экземпляров или статических методов [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], которые могут быть вызваны для экземпляра класса.  
  
## <a name="remarks"></a>Примечания  
 Класс позволяет создавать новые объекты, используя наследование на основе прототипа, конструкторы, методы экземпляров и статические методы. Объект `super` в конструкторе или методе класса позволяет вызывать такой же конструктор или метод, как и в родительском классе или объекте. Чтобы указать, методы какого класса или объекта должен унаследовать новый класс, добавьте после имени класса оператор `extends`.  
  
## <a name="example"></a>Пример  
  
```JavaScript  
class Spelunking extends EXPERIENCE.Outdoor {  
  constructor(name, location) {  
    super(name, location);  
  
    this.minSkill = Spelunking.defaultSkill();  
    //...  
  }  
  update(minSkill) {  
    //...  
    super.update(minSkill);  
  }  
  static defaultSkill() {  
    return new EXPERIENCE.Level3();  
  }  
}  
```  
  
## <a name="example"></a>Пример  
 Для классов можно также создавать имена вычисляемых свойств. В следующем примере кода имя вычисляемого свойства создается с помощью синтаксиса `set`.  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    set [propName](v) {  
        this.value = v;  
    }  
};  
  
var s = new Spelunking();  
console.log(s.value);  
s.prop_42 = 42;  
console.log(s.value);  
  
// Output:  
// undefined  
// 42  
  
```  
  
## <a name="example"></a>Пример  
 В следующем примере кода имя свойства для класса создается динамически с помощью синтаксиса `get`.  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    get [propName]() {  
        return 777;  
    }  
}  
  
var s = new Spelunking();  
console.log(s.prop_42);  
  
// Output:  
// 777  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12exp](../../javascript/reference/includes/jsv12exp-md.md)]