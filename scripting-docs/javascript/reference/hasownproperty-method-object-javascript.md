---
title: "Метод hasOwnProperty (Object) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- hasOwnProperty
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hasOwnProperty method
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 397b68fc87bf730886c928e099037ff0183a7f63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="hasownproperty-method-object-javascript"></a>Метод hasOwnProperty (Object) (JavaScript)
Определяет, содержит ли объект свойство с указанным именем.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## <a name="parameters"></a>Параметры  
 `object`  
 Обязательный. Экземпляр объекта.  
  
 `proName`  
 Обязательный. Строковое значение имени свойства.  
  
## <a name="remarks"></a>Примечания  
 `hasOwnProperty` Возвращает `true` Если `object` имеет свойство с указанным именем `false` Если это не так. Этот метод не проверяет свойства в цепочке прототипов объекта; свойство должно быть членом самого объекта.  
  
 Данное свойство не поддерживается для объектов узла для Internet Explorer 8 и ниже.  
  
## <a name="example"></a>Пример  
 В следующем примере все `String` объекты, совместно используют общий метод split. Следующий код будет выводить **false** и **true**.  
  
```JavaScript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор In](../../javascript/reference/in-operator-decrementjavascript.md)