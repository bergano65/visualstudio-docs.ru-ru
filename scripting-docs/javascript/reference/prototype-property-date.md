---
title: Свойство prototype (Date) | Документы Microsoft
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
ms.assetid: 44f9c637-7da7-4833-906d-358506f32ced
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c0b337964d2a2fe17a4e9a7906d81069470e61b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639224"
---
# <a name="prototype-property-date"></a>Свойство prototype (Date)
Возвращает ссылку на прототип для даты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
date.prototype  
```  
  
## <a name="remarks"></a>Примечания  
 Аргумент `date` является именем объекта.  
  
 Используйте `prototype` свойство, чтобы предоставить базовый набор функциональных возможностей в дату. Новые экземпляры объекта "наследуют" поведение прототипа, назначенного этому объекту.  
  
 Например, чтобы добавить метод в объект `Date`, возвращающий значение самого большого элемента массива, объявите функцию, добавьте ее в `Date.prototype`, а затем используйте его.  
  
```JavaScript  
function max( ){  
    var max = new Date();  
    max.setFullYear(2200, 01, 01);  
    return max;  
}  
Date.prototype.maxDate = max;  
var myDate = new Date();  
  
if (myDate < myDate.maxDate())  
    document.write("today isn't the max");  
else if (myDate == myDate.maxDate())  
    document.write("today is the max");   
  
// Output:  
// today isn't the max  
  
```  
  
 Все встроенные [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объекты имеют `prototype` свойство, которое доступно только для чтения. Свойства и методы могут быть добавлены в прототип, но объект нельзя назначить другому прототипу. Тем не менее определенных пользователем объектов можно назначить новый прототип.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]