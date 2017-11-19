---
title: "Свойство prototype (String) | Документы Microsoft"
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
ms.assetid: 437ce478-9c45-45f7-8952-bd71856cfcd8
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df8c6abbd64fce9172d805c2e22dee51f4fbbee4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-string"></a>Свойство prototype (String)
Возвращает ссылку на прототип класса строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
string.prototype  
```  
  
## <a name="remarks"></a>Примечания  
 `string` Аргумент является именем строки.  
  
 Чтобы для класса объектов обеспечить базовый набор функциональности, используйте свойство `prototype`. Новые экземпляры объекта "наследуют" поведение прототипа, назначенного этому объекту.  
  
 Например, чтобы добавить метод в `String` , возвращающий значение последнего элемента строки, объявите функцию, добавьте его в `String.prototype`, а затем использовать его.  
  
```JavaScript  
function string_last( ){  
    return this.charAt(this.length - 1);  
}  
String.prototype.last = string_last;  
var myString = new String("every good boy does fine");  
document.write(myString.last());  
  
// Output:  
// e  
```  
  
 Все встроенные [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объекты имеют `prototype` свойство, которое доступно только для чтения. Свойства и методы могут быть добавлены в прототип, но объект нельзя назначить другому прототипу. Тем не менее определенных пользователем объектов можно назначить новый прототип.  
  
 Списках методов и свойств для каждого встроенного объекта в этом справочнике по языку указывают, какие из них являются частью прототип объекта, а какие — нет.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]