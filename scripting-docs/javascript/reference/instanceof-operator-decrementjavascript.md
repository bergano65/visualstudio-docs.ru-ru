---
title: "Оператор instanceof (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: instanceof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: instanceOf operator
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 672047cb066a812d16edc693638c3d6d8295798b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="instanceof-operator-javascript"></a>Оператор instanceof (JavaScript)
Возвращает логическое значение, указывающее, является ли объект экземпляром определенного класса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = object instanceof class  
```  
  
## <a name="parameters"></a>Параметры  
 `result`  
 Обязательный. Любая переменная.  
  
 `object`  
 Обязательный. Любое выражение объекта.  
  
 `class`  
 Обязательный. Любой определенный класс объектов.  
  
## <a name="remarks"></a>Примечания  
 Оператор `instanceof` возвращает значение `true`, если объект, определяемый параметром `object`, является экземпляром класса, определяемого параметром `class`. Он возвращает значение `true`, если класс, определяемый параметром `true`, `class`присутствует в цепочке прототипов данного объекта. Он возвращает значение `false`, если объект, определяемый параметром `object`, не является экземпляром класса, определяемого параметром `class`, или параметр `object` имеет значение `null`.  
  
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