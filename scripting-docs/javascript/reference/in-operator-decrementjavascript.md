---
title: Оператор in (JavaScript) | Документы Microsoft
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
- in_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- in operator
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eefcd4c53d2e3366a26f0d8dfb099f59038507ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637454"
---
# <a name="in-operator-javascript"></a>Оператор in (JavaScript)
Проверяет существование свойства в объекте.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = property in object  
```  
  
## <a name="parameters"></a>Параметры  
 `result`  
 Обязательный. Любая переменная.  
  
 `property`  
 Обязательный. Выражение, результатом вычисления которого строкового выражения.  
  
 `object`  
 Обязательный. Любой объект.  
  
## <a name="remarks"></a>Примечания  
 `in` Оператор определяет, имеет ли объект свойство с именем `property`. Он также определяет, является ли свойство частью цепочки прототипов объекта. Дополнительные сведения о прототипы объектов см. в разделе [прототипы и наследование прототипов](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать `in` оператор:  
  
```JavaScript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)