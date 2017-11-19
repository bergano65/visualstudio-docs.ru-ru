---
title: "Оператор this (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: this_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- this statement
- constructors, referring to current object
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4afed1bd978d1985c151efa77873c93e699f0b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="this-statement-javascript"></a>Оператор this (JavaScript)
Ссылается на текущий объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
this.property  
```  
  
## <a name="remarks"></a>Примечания  
 Обязательный аргумент `property` — одно из свойств текущего объекта  
  
 Ключевое слово `this` можно использовать в конструкторах объекта для ссылки на текущий объект.  
  
## <a name="example"></a>Пример  
 В следующем примере **это** ссылается на вновь созданный объект Car и присваивает значения трем свойствам:  
  
```JavaScript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 **Это** ключевое слово обычно ссылается на **окна** объекта, если используется вне области любого другого объекта. Однако внутри обработчиков событий `this` ссылается на элемент DOM, вызвавший событие.  
  
 В следующем коде (для Internet Explorer 9 и более поздних версий) обработчик событий выводит строковую версию кнопки, которая имеет идентификатор элемента "clicker".  
  
```JavaScript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Использование метода bind](../../javascript/advanced/using-the-bind-method-javascript.md)