---
title: "Свойство Length (аргументы) (JavaScript) | Документы Microsoft"
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
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- length property (arguments)
- Length property
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cede75a91244442f5f28ec9f71b7128814bed5d2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-arguments-javascript"></a>Свойство length (аргументы) (JavaScript)
Возвращает фактическое количество аргументов, переданных функции вызывающим объектом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
[function.]arguments.length  
```  
  
## <a name="remarks"></a>Примечания  
 Необязательный *функция* аргумент — имя выполняющегося в данный момент `Function` объекта.  
  
 **Длина** свойство **аргументы** инициализировать объект обработчика скриптов на фактическое число аргументов, переданных `Function` объектов при начале выполнения этой функции.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **длина** свойство **аргументы** объекта. Чтобы полностью понять в примере, передайте в функцию, чем 2 аргументов, которые требуется большим числом аргументов:  
  
```JavaScript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Применяется к**: [объект arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Функции объекта](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство arguments (Function)](../../javascript/reference/arguments-property-function-javascript.md)   
 [Свойство Length (массив)](../../javascript/reference/length-property-array-javascript.md)   
 [Свойство length (строка)](../../javascript/reference/length-property-string-javascript.md)