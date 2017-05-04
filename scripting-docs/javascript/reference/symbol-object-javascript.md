---
title: "Объект Symbol (JavaScript) | Microsoft Docs"
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
ms.assetid: 2ad059f1-4b7f-4758-882a-c74ce1283ab0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Объект Symbol (JavaScript)
Позволяет создать уникальный идентификатор.  
  
## Синтаксис  
  
```  
obj = Symbol(desc)  
```  
  
#### Параметры  
 `desc`  
 Необязательно.  Описание символа.  
  
## Заметки  
 Объекты Symbol позволяют добавлять свойства в существующие объекты, исключая возможность создания помех существующим свойствам объектов, создания непредусмотренной области видимости и других несогласованных дополнений, которые могут быть реализованы другими частями кода.  
  
 Символ представляет собой примитивный тип данных.  Объекты Symbol нельзя создавать с помощью оператора `new`.  
  
 Для добавления объектов Symbol в реестр глобальных символов используйте функции `Symbol.for` и `Symbol.keyFor`.  При сериализации символов в виде строк используйте реестр глобальных символов, чтобы убедиться, что строки сопоставляются с правильными символами во всех случаях.  
  
 JavaScript включает следующие значения встроенных символов, которые доступны в глобальной области видимости.  
  
|Символ|Описание|  
|------------|--------------|  
|`Symbol.hasInstance`|Этот метод определяет, распознает ли объект конструктора объект как один из экземпляров конструктора.  Он используется внутренним образом оператором `instanceof`.|  
|`Symbol.isConcatSpreadable`|Это свойство возвращает логическое значение, указывающее, должен ли метод `Array.concat` сводить объект к его элементам массива.|  
|`Symbol.iterator`|Этот метод возвращает итератор по умолчанию для объекта.  Он используется внутренним образом оператором `for…of`.|  
|`Symbol.toPrimitive`|Этот метод преобразует объект в соответствующее значение примитива.  Он используется внутренним образом абстрактной операцией `ToPrimitive`.|  
|`Symbol.toStringTag`|Это свойство возвращает строковое значение, которое используется для создания строкового описания объекта по умолчанию.  Он используется внутренним образом встроенным методом `Object.toString`.|  
|`Symbol.unscopables`|Это свойство возвращает объект, свойства которого исключены из привязок среды `with` для связанного объекта.|  
  
## Функции  
 В следующей таблице перечислены функции объекта `Symbol`.  
  
|||  
|-|-|  
|Свойство|Описание|  
|[Symbol.For](../../javascript/reference/symbol-for-function-javascript.md)|Возвращает символ для указанного ключа или, если этот ключ отсутствует, создает новый объект Symbol с новым ключом.|  
|[Symbol.keyFor](../../javascript/reference/symbol-keyfor-function-javascript.md)|Возвращает ключ для указанного символа.|  
|||  
  
## Пример  
  
```javascript  
(function() {  
  
    // module-scoped symbol  
    var key = Symbol("description");  
  
    function MyClass(privateData) {  
      this[key] = privateData;  
    }  
  
    MyClass.prototype = {  
      someFunc: function() {  
        return "data: " + this[key];  
      }  
    };  
  
    var c = new MyClass("private data")  
    console.log(key);  
    console.log(c["key"]);  
    console.log(c.someFunc());  
  
})();  
  
// Output:  
// undefined  
// undefined  
// data: private data  
```  
  
## Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]