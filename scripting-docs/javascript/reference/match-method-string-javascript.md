---
title: Метод Match (String) (JavaScript) | Документы Microsoft
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
- match
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Match method
ms.assetid: eda9ad27-4f9b-4cb1-8345-a0ae85979ca0
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46727942d73779351f1c0cceaf2eb90a691a8ebe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639374"
---
# <a name="match-method-string-javascript"></a>Метод match (String) (JavaScript)
Соответствует строке регулярного выражения и возвращает массив, содержащий результаты поиска.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
stringObj.match(rgExp)   
```  
  
## <a name="parameters"></a>Параметры  
 `stringObj`  
 Обязательный. `String` Или строковый литерал, в котором выполняется поиск.  
  
 `rgExp`  
 Обязательный. Объект регулярного выражения, который содержит шаблон регулярного выражения и установленные флаги. Это также может быть имя переменной или строковым литералом, содержащий шаблон регулярного выражения и флаги.  
  
## <a name="remarks"></a>Примечания  
 Если `match` метод не найден, возвращается значение `null`. При обнаружении совпадения, `match` возвращает массив, а свойства глобального `RegExp` объекта будут обновлены в соответствии с результатами совпадения.  
  
 Если глобальный флаг (`g`) не задано, элемент нулевой массива содержит полное совпадение, элементы с 1 по  *n*  содержат только вложенные совпадения. Это происходит так же, как поведение [метод exec (Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md) при глобальный флаг не установлен. Если глобальный флаг имеет значение, 0 элементов с помощью  *n*  содержат все найденные совпадения.  
  
 Если глобальный флаг не установлен, массив, возвращаемый методом `match` метод имеет два свойства `input` и `index`. `input` Свойство содержит весь искомая строка. `index` Свойство содержит позицию сопоставленной подстроки в пределах завершения искомая строка.  
  
 Если флаг `i` не установлен, при поиске не учитывается регистр.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `match`.  
  
```JavaScript  
var src = "azcafAJAC";  
  
var re = /[a-c]/;  
  
var result = src.match(re);  
  
// The entire match is in array element 0.  
document.write(result[0] + "<br/>");  
  
// Now try the same match with the global flag.  
var reg = /[a-c]/g;  
result = src.match(reg);  
  
// The matches are in elements 0 through n.  
for (var index = 0; index < result.length; index++)  
{  
    document.write ("submatch " + index + ": " +  result[index]);  
    document.write("<br />");  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применяется к**: [строковый объект](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод exec (Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Объект RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Метод replace (строка)](../../javascript/reference/replace-method-string-javascript.md)   
 [Метод Search (String)](../../javascript/reference/search-method-string-javascript.md)   
 [Метод Test (Regular Expression)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Программирование регулярных выражений (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Чередование и части выражений (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Обратные ссылки (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)