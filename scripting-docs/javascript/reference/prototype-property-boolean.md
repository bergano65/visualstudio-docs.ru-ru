---
title: Свойство prototype (Boolean) | Документы Microsoft
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
ms.assetid: e4f07cb5-3462-488c-a418-76064ab10eae
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52d2d241c4d550fe4491ea827fab9d586281242d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638844"
---
# <a name="prototype-property-boolean"></a>Свойство prototype (Boolean)
Возвращает ссылку на прототип для логического значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
boolean.prototype  
```  
  
## <a name="remarks"></a>Примечания  
 Аргумент `boolean` является именем объекта.  
  
 Свойство `prototype` обеспечивает основной набор функций для класса объектов. Новые экземпляры объекта "наследуют" поведение прототипа, назначенного этому объекту. В прототип можно добавить свойства и методы, однако встроенные объекты нельзя назначить другому прототипу.  
  
 Например, чтобы добавить метод в объект `Boolean`, возвращающий значение самого большого элемента массива, объявите функцию, добавьте ее в `Boolean.prototype`, а затем используйте его.  
  
```JavaScript  
function isFalse( ){  
    if (this.toString() == "false")  
         return true;  
    else  
        return false;  
}  
Boolean.prototype.isFalse = isFalse;  
var bool = new Boolean(1);  
document.write(bool.isFalse());  
  
// Output:  
// false  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]