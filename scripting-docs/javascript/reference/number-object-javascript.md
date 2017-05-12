---
title: "Объект Number (JavaScript) | Microsoft Docs"
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
  - "Number_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Number - объект"
ms.assetid: 76e87c37-cf6c-46cc-bafa-04be1fe3d78d
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Объект Number (JavaScript)
Объект, представляющий число любого рода.  Все числа в JavaScript представляют собой 64\-разрядные числа с плавающей запятой.  
  
## Синтаксис  
  
```  
  
numObj = new Number(value)  
```  
  
## Параметры  
 `numObj`  
 Обязательный.  Имя переменной, которой присваивается объект `Number`.  
  
 `value`  
 Обязательный.  Числовое значение.  
  
## Заметки  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] создает объекты `Number`, когда переменной присваивается числовое значение, например `var num = 255.336;`.  Создание объектов `Number` явным образом требуется крайне редко.  
  
 Наряду со свойствами и методами, унаследованными от объекта `Object`, объект `Number` имеет собственные свойства и методы.  В некоторых случаях объекты Number преобразуются в строки, например, когда число прибавляется к строке или сцепляется со строкой, а также при использовании метода `toString`.  Дополнительные сведения см. в статье [Оператор сложения \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md).  
  
 В JavaScript имеется несколько числовых констант.  Полный список см. в статье [Числовые константы](../../javascript/reference/number-constants-javascript.md).  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Свойства  
 В следующей таблице перечислены свойства объекта `Number` .  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Свойство constructor](../../javascript/reference/constructor-property-object-javascript.md)|Указывает функцию, которая создает объект.|  
|[Свойство prototype](../../javascript/reference/prototype-property-object-javascript.md)|Возвращает ссылку на прототип класса объектов.|  
  
## Функции  
 В следующей таблице перечислены функции объекта `Number` .  
  
|Функция|Описание|  
|-------------|--------------|  
|[Функция Number.isFinite](../../javascript/reference/number-isfinite-function-number-javascript.md)|Возвращает логическое значение, указывающее, является ли значение конечным.|  
|[Функция Number.isInteger](../../javascript/reference/number-isinteger-function-number-javascript.md)|Возвращает логическое значение, указывающее, является ли значение целым числом.|  
|[Функция Number.isNaN](../../javascript/reference/number-isnan-function-number-javascript.md)|Возвращает логическое значение, указывающее, является ли значение зарезервированным значением `NaN` \(не числом\).|  
|[Функция Number.isSafeInteger](../../javascript/reference/number-issafeinteger-number-javascript.md)|Возвращает логическое значение, указывающее, можно ли безопасно представить значение в JavaScript.|  
  
## Методы  
 В следующей таблице перечислены методы объекта `Number` .  
  
|Метод|Описание|  
|-----------|--------------|  
|[Метод hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Возвращает логическое значение, указывающее, содержит ли объект свойство с указанным именем.|  
|[Метод isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Возвращает логическое значение, указывающее, существует ли объект в иерархии прототипов другого объекта.|  
|[Метод propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Возвращает логическое значение, определяющее, является ли указанное свойство частью объекта, и является ли оно перечислимым.|  
|[Метод toExponential](../../javascript/reference/toexponential-method-number-javascript.md)|Возвращает строку, которая содержит число, представленное в экспоненциальной нотации.|  
|[Метод toFixed](../../javascript/reference/tofixed-method-number-javascript.md)|Возвращает строку, представляющую число в нотации с фиксированной запятой.|  
|[Метод toLocaleString](../../javascript/reference/tolocalestring-number.md)|Возвращает объект, преобразованный в строку на основе текущего языкового стандарта.|  
|[Метод toPrecision](../../javascript/reference/toprecision-method-number-javascript.md)|Возвращает строку, которая содержит число, представленное в экспоненциальной нотации или в нотации с фиксированной запятой с указанным числом знаков.|  
|[Метод toString](../../javascript/reference/tostring-method-object-javascript.md)|Возвращает строковое представление объекта.|  
|[Метод valueOf](../../javascript/reference/valueof-method-object-javascript.md)|Возвращает примитивное значение указанного объекта.|  
  
## См. также  
 [Объекты JavaScript](../../javascript/reference/javascript-objects.md)   
 [Объект Math](../../javascript/reference/math-object-javascript.md)   
 [Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)