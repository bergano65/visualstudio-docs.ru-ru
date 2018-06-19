---
title: Символ объекта (JavaScript) | Документы Microsoft
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
ms.assetid: 2ad059f1-4b7f-4758-882a-c74ce1283ab0
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd755d5b753eb91b89b869645287685a97f8f571
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641304"
---
# <a name="symbol-object-javascript"></a>Объект Symbol (JavaScript)
Позволяет создать уникальный идентификатор.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
obj = Symbol(desc)  
```  
  
#### <a name="parameters"></a>Параметры  
 `desc`  
 Необязательно. Описание символа.  
  
## <a name="remarks"></a>Примечания  
 Объекты Symbol позволяют добавлять свойства в существующие объекты, исключая возможность создания помех существующим свойствам объектов, создания непредусмотренной области видимости и других несогласованных дополнений, которые могут быть реализованы другими частями кода.  
  
 Символ представляет собой примитивный тип данных. Объекты Symbol нельзя создавать с помощью оператора `new`.  
  
 Для добавления объектов Symbol в реестр глобальных символов используйте функции `Symbol.for` и `Symbol.keyFor`. При сериализации символов в виде строк используйте реестр глобальных символов, чтобы убедиться, что строки сопоставляются с правильными символами во всех случаях.  
  
 JavaScript включает следующие значения встроенных символов, которые доступны в глобальной области видимости.  
  
|Символ|Описание|  
|------------|-----------------|  
|`Symbol.hasInstance`|Этот метод определяет, распознает ли объект конструктора объект как один из экземпляров конструктора. Он используется внутренним образом оператором `instanceof`.|  
|`Symbol.isConcatSpreadable`|Это свойство возвращает логическое значение, указывающее, должен ли метод `Array.concat` сводить объект к его элементам массива.|  
|`Symbol.iterator`|Этот метод возвращает итератор по умолчанию для объекта. Он используется внутренним образом оператором `for...of`.|  
|`Symbol.toPrimitive`|Этот метод преобразует объект в соответствующее значение примитива. Он используется внутренним образом абстрактной операцией `ToPrimitive`.|  
|`Symbol.toStringTag`|Это свойство возвращает строковое значение, которое используется для создания строкового описания объекта по умолчанию. Он используется внутренним образом встроенным методом `Object.toString`.|  
|`Symbol.unscopables`|Это свойство возвращает объект, свойства которого исключены из привязок среды `with` для связанного объекта.|  
  
## <a name="functions"></a>Функции  
 В следующей таблице перечислены функции объекта `Symbol`.  
  
|||  
|-|-|  
|Свойство|Описание|  
|[Symbol.For](../../javascript/reference/symbol-for-function-javascript.md)|Возвращает символ для указанного ключа или, если этот ключ отсутствует, создает новый объект Symbol с новым ключом.|  
|[Symbol.keyFor](../../javascript/reference/symbol-keyfor-function-javascript.md)|Возвращает ключ для указанного символа.|  
|||  
  
## <a name="example"></a>Пример  
  
```JavaScript  
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
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]