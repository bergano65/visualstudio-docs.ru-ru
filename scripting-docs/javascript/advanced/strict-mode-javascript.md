---
title: "Строгий режим (JavaScript) | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1038
- VS.WebClient.Help.SCRIPT1050
- VS.WebClient.Help.SCRIPT1042
- VS.WebClient.Help.SCRIPT1041
- VS.WebClient.Help.SCRIPT1046
- VS.WebClient.Help.SCRIPT1045
- VS.WebClient.Help.SCRIPT1037
- VS.WebClient.Help.SCRIPT1039
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strict mode
- use strict
ms.assetid: 0f27022a-f41c-4504-965c-5a2701f342cd
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 77ee7d54dd265026b2bf4c9af52a71cccf9a7675
ms.contentlocale: ru-ru
ms.lasthandoff: 08/11/2017

---
# <a name="strict-mode-javascript"></a>Строгий режим (JavaScript)
Строгий режим — это способ обеспечения более тщательной проверки ошибок в коде. В строгом режиме нельзя, например, использовать неявно объявляемые переменные, присваивать значения свойствам, доступным только для чтения, и добавлять свойства в объекты, которые не являются расширяемыми. Ограничения перечислены ниже в подразделе [Ограничения, налагаемые на код в строгом режиме](../../javascript/advanced/strict-mode-javascript.md#rest). Дополнительные сведения о строгом режиме см. в документе [Спецификация языка ECMAScript, 5-й выпуск](http://www.ecma-international.org/publications/standards/Ecma-262.htm).  
  
> [!WARNING]
>  В версиях Internet Explorer до Internet Explorer 10 строгий режим не поддерживается.  
  
## <a name="declaring-strict-mode"></a>Объявление строгого режима  
 Объявить строгий режим можно путем добавления директивы `"use strict";` в начале файла, программы или функции. Объявление такого типа называется *пролог директивы*. Область объявления строгого режима зависит от его контекста. Если он объявляется в глобальном контексте (вне области функции), весь код в программе находится в строгом режиме. Если он объявляется в функции, весь код в этой функции находится в строгом режиме. В следующем примере весь код находится в строгом режиме, и объявление переменной за пределами функции приводит к появлению синтаксической ошибки "Неопределенная переменная в строгом режиме".  
  
```JavaScript  
"use strict";  
function testFunction(){  
    var testvar = 4;  
    return testvar;  
}  
  
// This causes a syntax error.  
testvar = 5;  
  
```  
  
 В следующем примере в строгом режиме находится только код внутри функции `testFunction`. Объявление переменной за пределами функции не приведет к синтаксической ошибке, а объявление внутри функции приведет к такой ошибке.  
  
```JavaScript  
function testFunction(){  
    "use strict";  
    // This causes a syntax error.  
    testvar = 4;  
    return testvar;  
}  
testvar = 5;  
  
```  
  
<a name="rest"></a>   
## <a name="restrictions-on-code-in-strict-mode"></a>Ограничения, налагаемые на код в строгом режиме  
 В приведенной ниже таблице перечислены наиболее важные ограничения, применяемые в строгом режиме.  
  
|||||  
|-|-|-|-|  
|**Элемент языка**|**Ограничение**|**Ошибка**|**Пример**|  
|Переменная|Использование переменной без ее объявления.|SCRIPT5042. Неопределенная переменная в строгом режиме|`testvar = 4;`|  
|Свойство только для чтения|Запись в свойство, доступное только для чтения.|SCRIPT5045. Присвоение значений свойствам только для чтения в режиме strict запрещено|`var testObj = Object.defineProperties({}, {     prop1: {         value: 10,         writable: false // by default     },     prop2: {         get: function () {         }     } }); testObj.prop1 = 20;  testObj.prop2 = 30;`|  
|Нерасширяемое свойство|Добавление свойства в объект, атрибуту `extensible` которого присвоено значение `false`.|SCRIPT5046. Не удается создать свойство для нерасширяемого объекта|`var testObj = new Object();  Object.preventExtensions(testObj);  testObj.name = "Bob";`|  
|`delete`|Удаление переменной, функции или аргумента.<br /><br /> Удаление свойства, атрибуту `configurable` которого присвоено значение `false`.|SCRIPT1045. В строгом режиме запрещен вызов удаления для \<выражение>|`var testvar = 15; function testFunc() {}; delete testvar; delete testFunc;  Object.defineProperty(testObj, "testvar", {     value: 10,     configurable: false     }); delete testObj.testvar;`|  
|Дублирование свойства|Определение свойства в литерале объекта более одного раза.|SCRIPT1046. В строгом режиме запрещено задавать несколько определений одного свойства|`var testObj = {     prop1: 10,     prop2: 15,     prop1: 20 };`|  
|Дублирование имени параметра|Использование имени параметра в функции более одного раза.|SCRIPT1038. В строгом режиме запрещены повторяющиеся имена формальных параметров|`function testFunc(param1, param1) {     return 1; };`|  
|Ключевые слова, зарезервированные на будущее|Использование зарезервированного на будущее ключевого слова в качестве имени переменной или функции.|SCRIPT1050. Недопустимо использовать в качестве идентификатора зарезервированное на будущее слово. В строгом режиме имя идентификатора зарезервировано.|-                      `implements`<br /><br /> -                      `interface`<br /><br /> -                      `package`<br /><br /> -                      `private`<br /><br /> -                      `protected`<br /><br /> -                      `public`<br /><br /> -                      `static`<br /><br /> -                      `yield`|  
|Восьмеричные числа|Присвоение восьмеричного значения числовому литералу или попытка использовать escape-символ в восьмеричном значении.|SCRIPT1039. В строгом режиме запрещены восьмеричные цифровые литералы и escape-символы|`var testoctal = 010; var testescape = \010;`|  
|`this`|Значение `this` не преобразуется в глобальный объект, когда оно равно `null` или `undefined`.||`function testFunc() {     return this; } var testvar = testFunc();`<br /><br /> В нестрогом режиме значение `testvar` является глобальным объектом, а в строгом режиме оно равно `undefined`.|  
|`eval` в качестве идентификатора|Строку "eval" нельзя использовать в качестве идентификатора (имени переменной или функции, имени параметра и т. п.).||`var eval = 10;`|  
|Функция, объявленная внутри оператора или блока|Объявить функцию внутри оператора или блока нельзя.|SCRIPT1047. В строгом режиме объявления функций не могут располагаться внутри других операторов или блоков. Они могут располагаться только на верхнем уровне или непосредственно внутри тела другой функции.|`var arr = [1, 2, 3, 4, 5]; var index = null; for (index in arr) {     function myFunc() {}; }`|  
|Переменная, объявленная внутри функции `eval`|Если переменная объявлена внутри функции `eval`, она не может использоваться за пределами этой функции.|SCRIPT1041. Недопустимое использование eval в строгом режиме|`eval("var testvar = 10"); testvar = 15;`<br /><br /> Косвенная оценка возможна, но по-прежнему невозможно использовать переменную, объявленную за пределами функции `eval`.<br /><br /> `var indirectEval = eval; indirectEval("var testvar = 10;"); document.write(testVar);`<br /><br /> Этот код приводит к появлению ошибки SCRIPT5009: переменная testVar не определена.|  
|`Arguments` в качестве идентификатора|Строку "arguments" нельзя использовать в качестве идентификатора (имени переменной или функции, имени параметра и т. п.).|SCRIPT1042. Недопустимое использование arguments в строгом режиме|`var arguments = 10;`|  
|`arguments` внутри функции|Изменять значения членов локального объекта `arguments` нельзя.||`function testArgs(oneArg) {     arguments[0] = 20; }`<br /><br /> В нестрогом режиме можно изменить значение параметра `oneArg` путем изменения значения `arguments[0]`, чтобы значения параметров `oneArg` и `arguments[0]` были равны 20. В строгом режиме изменение значения `arguments[0]` не влияет на значение `oneArg`, поскольку объект `arguments` представляет собой просто локальную копию.|  
|`arguments.callee`|Не допускается.||`function (testInt) {     if (testInt-- == 0)         return;     arguments.callee(testInt--); }`|  
|`with`|Не допускается.|SCRIPT1037. В строгом режиме запрещены операторы with|`with (Math){     x = cos(3);     y = tan(7); }`|
