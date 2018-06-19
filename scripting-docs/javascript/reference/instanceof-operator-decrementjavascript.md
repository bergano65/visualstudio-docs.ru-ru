---
title: Оператор instanceof (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- instanceof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- instanceOf operator
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b2124fe815c89c3c157be3ea729fa7edb9d96b39
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2018
ms.locfileid: "27799590"
---
# <a name="instanceof-operator-javascript"></a>Оператор instanceof (JavaScript)
Возвращает логическое значение, указывающее, является ли объект экземпляром определенного класса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = object instanceof class  
```  
  
## <a name="parameters"></a>Параметры  
 `result`  
 Обязательно. Любая переменная.  
  
 `object`  
 Обязательно. Любое выражение объекта.  
  
 `class`  
 Обязательно. Любой определенный класс объектов.  
  
## <a name="remarks"></a>Примечания  
 Оператор `instanceof` возвращает значение `true`, если объект, определяемый параметром `object`, является экземпляром класса, определяемого параметром `class`. Он возвращает `true` Если `class` присутствует в цепочке прототипов объекта. Он возвращает значение `false`, если объект, определяемый параметром `object`, не является экземпляром класса, определяемого параметром `class`, или параметр `object` имеет значение `null`.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование оператора `instanceof`.  
  
```JavaScript  
function objTest(obj){  
    var i, t, s = "";  
    t = new Array();  
    t["Date"] = Date;  
    t["Object"] = Object;  
    t["Array"] = Array;  
        for (i in t){  
            if (obj instanceof t[i]) {   
                s += "obj is an instance of " + i + "<br/>";  
            }  
            else {  
                s += "obj is not an instance of " + i + "<br/>";  
        }  
    }  
    return(s);  
}  
  
var obj = new Date();  
document.write(objTest(obj));  
  
// Output:   
// obj is an instance of Date  
// obj is an instance of Object  
// obj is not an instance of Array  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)