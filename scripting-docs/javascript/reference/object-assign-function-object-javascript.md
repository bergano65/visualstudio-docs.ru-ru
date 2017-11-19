---
title: "Функция Object.Assign (Object) (JavaScript) | Документы Microsoft"
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
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c156369299e58eac556d43a87476de2ce09173e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="objectassign-function-object-javascript"></a>Функция Object.assign (Object) (JavaScript)
Копирует значения из одного или нескольких исходных объектов в целевой объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Object.assign(target, ...sources );  
```  
  
#### <a name="parameters"></a>Параметры  
 `target`  
 Обязательный. Объект, в который копируются перечисляемые свойства.  
  
 `...sources`  
 Обязательный. Один или несколько объектов, из которых копируются перечислимые свойства.  
  
## <a name="exceptions"></a>Исключения  
 Эта функция выдает `TypeError`, если возникает ошибка назначения, которая завершает операцию копирования. `TypeError` выдается, если целевое свойство недоступно для записи.  
  
## <a name="remarks"></a>Примечания  
 Эта функция возвращает целевой объект. Только *перечислимые собственные* свойства копируются из исходного объекта к целевому объекту. Эту функцию можно использовать для слияния и клонирования объектов.  
  
 Источники `null` или `undefined` обрабатываются как пустые объекты и ничего не добавляют целевому объекту.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как объединить объект с помощью функции `Object.assign`.  
  
```JavaScript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как клонировать объект с помощью функции `Object.assign`.  
  
```JavaScript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]