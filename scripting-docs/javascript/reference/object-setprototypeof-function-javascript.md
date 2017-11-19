---
title: "Функция Object.setPrototypeOf (JavaScript) | Документы Microsoft"
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
ms.assetid: a2609f6e-aeee-4c13-b7cf-c31ddf58ff35
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 686fea255978b34af13fcf64785819f3d3afadbb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="objectsetprototypeof-function-javascript"></a>Функция Object.setPrototypeOf (JavaScript)
Задает прототип объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Object.setPrototypeOf(obj, proto);  
```  
  
#### <a name="parameters"></a>Параметры  
 `obj`  
 Обязательный. Объект, для которого задается прототип.  
  
 `proto`  
 Обязательный. Новый объект прототипа.  
  
## <a name="remarks"></a>Примечания  
  
> [!WARNING]
>  Задание прототипа может снизить производительность всей части кода JavaScript, которая обращается к объекту с измененным прототипом.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано задание прототипа для объекта.  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(Object.setPrototypeOf(rec) === Rectangle.prototype);  // Returns true  
    Object.getPrototypeOf(rec, Object.prototype);  
    console.log(Object.setPrototypeOf(rec) === Rectangle.prototype);  // Returns false  
}  
```  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано добавление свойств в объект путем их добавления в прототип.  
  
```JavaScript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
Object.setPrototypeOf(obj, proto);  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## <a name="example"></a>Пример  
 Следующий пример кода добавляет свойства в объект `String`, задавая для него новый прототип.  
  
```JavaScript  
var stringProp = { desc: "description" };  
  
Object.setPrototypeOf(String, stringProp);  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    Object.setPrototypeOf(s1, String); // Can't be set.  
    Object.setPrototypeOf(s2, String);  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]