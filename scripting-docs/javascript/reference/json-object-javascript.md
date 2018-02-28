---
title: "Объект JSON (JavaScript) | Документы Microsoft"
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
- JSON
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JSON object
ms.assetid: 0279a0e0-70bf-451a-a78e-0da4e2fdeb9a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5310132368f665c6734c469a67636d33a08858d4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="json-object-javascript"></a>Объект JSON (JavaScript)
Встроенный объект, предоставляющий функции для преобразования значений [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] в формат JSON (нотация объектов JavaScript) и обратно. Функция `JSON.stringify` сериализует значение [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] в текст JSON. Функция `JSON.parse` десериализует текст JSON для получения значения [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
JSON.[method]  
  
```  
  
## <a name="parameters"></a>Параметры  
 `Method`  
 Обязательный. Имя одного из методов объекта `JSON`.  
  
## <a name="remarks"></a>Примечания  
 Создать объект `JSON` с помощью оператора `new` невозможно. При попытке это сделать возникает ошибка. Тем не менее можно переопределить или изменить объект `JSON`.  
  
 Обработчик скриптов создает объект `JSON` при загрузке обработчика. Скрипту всегда доступны его методы.  
  
 При использовании встроенного объекта `JSON` следите за тем, чтобы он не был переопределен другим объектом `JSON`, определенным в скрипте. Может потребоваться изменить существующие операторы скрипта, которые обнаруживают наличие объекта `JSON`, поскольку у этих операторов будет другой результат вычисления. Это показано в следующем примере.  
  
```JavaScript  
if (!this.JSON) {  
    // JSON object does not exist.  
    }  
```  
  
 В примере выше результатом `!this.JSON` в [!INCLUDE[jsv58text](../../javascript/reference/includes/jsv58text-md.md)] является значение false. Поэтому код внутри оператора `if` не выполняется.  
  
## <a name="functions"></a>Функции  
 [Функция JSON.parse](../../javascript/reference/json-parse-function-javascript.md)  
  
 [Функция JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод toJSON (Date)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Объекты JavaScript](../../javascript/reference/javascript-objects.md)   
 [Пример приложения шаблона концентратора (магазин Windows)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)