---
title: Свойство Length (функция) (JavaScript) | Документы Microsoft
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
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Length property
- length property (function)
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fbd0334c18da2c6ef8de8366555d79f791e6855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637834"
---
# <a name="length-property-function-javascript"></a>Свойство length (функция) (JavaScript)
Возвращает число аргументов, определенных для функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
functionName.length  
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая *functionName* имя функции.  
  
 **Длина** свойства функции инициализируется обработчиком сценариев число аргументов в определении функции, когда создается экземпляр функции.  
  
 Что происходит при вызове функции с числом аргументов, отличных от значения его **длина** свойство зависит от функции.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **длина** свойство:  
  
```JavaScript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Свойство arguments (Function)](../../javascript/reference/arguments-property-function-javascript.md)   
 [Свойство Length (массив)](../../javascript/reference/length-property-array-javascript.md)   
 [Свойство length (строка)](../../javascript/reference/length-property-string-javascript.md)