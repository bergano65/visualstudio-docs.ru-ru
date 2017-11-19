---
title: "Свойство __proto__ (Object) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __proto__
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e38669c400acba6f4ed3c4ee3fb5836c31b1bc00
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="proto-property-object-javascript"></a>__proto__ свойство (Object) (JavaScript)
Содержит ссылку на внутренний прототип указанного объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
object.__proto__  
```  
  
#### <a name="parameters"></a>Параметры  
 `object`  
 Обязательный. Объект, для которого задается прототип.  
  
## <a name="remarks"></a>Примечания  
 `__proto__` Свойство может использоваться для установки прототипа для объекта.  
  
 Объект или функцию наследует все методы и свойства нового прототипа, а также все методы и свойства в цепочке прототипов новый прототип. Объект может иметь только один прототип (не включая унаследованные прототипов в цепочке прототипов), поэтому при вызове `__proto__` свойство, замените предыдущих прототипа.  
  
 Прототип можно задать только для расширяемого объекта. Дополнительные сведения см. в разделе [функция Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md).  
  
> [!NOTE]
>  `__proto__` Имя свойства начинается и заканчивается с двух символов подчеркивания.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано задание прототипа для объекта.  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано добавление свойств в объект путем их добавления в прототип.  
  
```JavaScript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
obj.__proto__ = proto;  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## <a name="example"></a>Пример  
 Следующий пример кода добавляет свойства в объект `String`, задавая для него новый прототип.  
  
```JavaScript  
var stringProp = { desc: "description" };  
  
String.__proto__ = stringProp;  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    s1.__proto__ = String;  // Can't be set.  
    s2.__proto__ = String;  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Прототипы и наследование прототипов](../../javascript/advanced/prototypes-and-prototype-inheritance.md)