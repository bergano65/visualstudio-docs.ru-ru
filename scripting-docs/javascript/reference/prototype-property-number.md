---
title: "Свойство prototype (Number) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d5fb87af-fc3a-4469-8dde-d31daf654f94
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dba8b8886b4fdbc48a662796863b1dfca019aec
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-number"></a>Свойство prototype (Number)
Возвращает ссылку на прототип класса числа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
number.prototype  
```  
  
## <a name="remarks"></a>Примечания  
 `number` Аргумент является именем числа.  
  
 Чтобы для класса объектов обеспечить базовый набор функциональности, используйте свойство `prototype`. Новые экземпляры объекта "наследуют" поведение прототипа, назначенного этому объекту.  
  
 Например, чтобы добавить метод в `Number` , возвращающий цифр номера (целого числа со знаком), объявите функцию, добавьте его в `Number.prototype`, а затем использовать его.  
  
```JavaScript  
function number_digits() {  
    var digits = 0;  
    var num = this;  
    while (num) >= 1) {  
        digits++;  
        num /= 10;  
    }  
    return digits;  
}  
  
Number.prototype.digits = number_digits;  
var myNumber = new Number(3456.789);  
document.write(myNumber.digits());  
// Output:  
// 4  
```  
  
 Все встроенные [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объекты имеют `prototype` свойство, которое доступно только для чтения. Свойства и методы могут быть добавлены в прототип, но объект нельзя назначить другому прототипу. Тем не менее определенных пользователем объектов можно назначить новый прототип.  
  
 Списках методов и свойств для каждого встроенного объекта в этом справочнике по языку указывают, какие из них являются частью прототип объекта, а какие — нет.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]