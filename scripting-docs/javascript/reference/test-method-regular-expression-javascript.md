---
title: Метод Test (Regular Expression) (JavaScript) | Документы Microsoft
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
- test
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- test method
ms.assetid: 4f4b6e39-cb1a-4be9-a66f-7b846075580d
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53e2d2c23821cba5149367c7b5a735fa471bf581
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640754"
---
# <a name="test-method-regular-expression-javascript"></a>Метод test (Regular Expression) (JavaScript)
Возвращает логическое значение, указывающее, существует ли шаблон в строке для поиска.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
rgExp.test(str)   
```  
  
## <a name="parameters"></a>Параметры  
 `rgExp`  
 Обязательный. Экземпляр **регулярное выражение** объект, содержащий шаблон регулярного выражения и установленные флаги.  
  
 `str`  
 Обязательный. Строка, в которой выполняется поиск.  
  
## <a name="remarks"></a>Примечания  
 **Тестирования** метод проверяет, если шаблон существует в строке и возвращает **true** в этом случае и **false** в противном случае.  
  
 Свойства глобального `RegExp` не изменяет объект **тестирования** метод.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **тестирования** метод. Чтобы использовать этот пример, передайте функции шаблон регулярного выражения и строку. Функция будет тестирования вхождение шаблон регулярного выражения в строке и возвращает строку, указывающую результаты поиска:  
  
```JavaScript  
function TestDemo(re, teststring)  
{  
   // Test string for existence of regular expression.  
   var found = re.test(teststring)  
  
   // Format the output.  
   var s = "";  
   s += "'" + teststring + "'"  
  
   if (found)  
      s += " contains ";  
   else  
      s += " does not contain ";  
  
   s += "'" + re.source + "'"  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применяется к**: [объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Объект RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярного выражения (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)