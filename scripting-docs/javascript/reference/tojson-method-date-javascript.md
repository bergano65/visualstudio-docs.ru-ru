---
title: Метод toJSON (Date) (JavaScript) | Документы Microsoft
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
helpviewer_keywords:
- toJSON method
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a131c7b248ca0486ab0b3b02d40e4351136c37c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641294"
---
# <a name="tojson-method-date-javascript"></a>Метод toJSON (Date) (JavaScript)
Используемые [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md) способ включения преобразование данных объекта для сериализации JavaScript Object Notation (JSON).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
objectname.toJSON()  
```  
  
## <a name="parameters"></a>Параметры  
 `objectname`  
 Обязательный. Объект, для которого JSON нужен сериализации.  
  
## <a name="remarks"></a>Примечания  
 `toJSON` Используется метод `JSON.stringify` функции. `JSON.stringify`Сериализует [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] значение в текст JSON. Если `toJSON` метод предоставляется для `JSON.stringify`, `toJSON` метод вызывается, когда `JSON.stringify` вызывается.  
  
 `toJSON` Метод является членом встроенной [даты](../../javascript/reference/date-object-javascript.md) [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объекта. Он возвращает строку даты в формате ISO для часового пояса UTC (обозначаемая суффиксом Z).  
  
 Можно переопределить `toJSON` метод `Date` типа или определите `toJSON` метод для других типов объектов для достижения преобразований данных для конкретного типа объекта перед выполнением сериализации JSON.  
  
## <a name="example"></a>Пример  
 В следующем примере используется `toJSON` метод сериализации строковых значений элементов в верхнем регистре. `toJSON` Метод вызывается, когда `JSON.stringify` вызывается.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
  
/* The value of jsonText is:  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## <a name="example"></a>Пример  
 Следующий пример показывает, как использовать `toJSON` метод, который является членом встроенной [даты](../../javascript/reference/date-object-javascript.md) объекта.  
  
```JavaScript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]**Применяется к:** [объект даты](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Объект JSON](../../javascript/reference/json-object-javascript.md)   
 [Функция JSON.parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Функция JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)   
 [Методы JavaScript](../../javascript/reference/javascript-methods.md)