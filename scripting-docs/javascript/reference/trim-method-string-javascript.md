---
title: "Метод Trim (String) (JavaScript) | Документы Microsoft"
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
helpviewer_keywords: trim method
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de358981cfbf569ef35be95b55b3e9856027df35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="trim-method-string-javascript"></a>Метод trim (String) (JavaScript)
Удаляет из строки начальные и конечные пробелы и символы конца строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
stringObj.trim()  
```  
  
## <a name="parameters"></a>Параметры  
 `stringObj`  
 Обязательный. Объект `String` или строковый литерал. Эта строка не изменяется методом `trim`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Исходная строка с удаленными начальными и конечными пробелами и символами конца строки.  
  
## <a name="remarks"></a>Примечания  
 К удаляемым символам относятся пробел, символ табуляции, перевод страницы, возврат каретки и перевод строки. В разделе [специальные символы](../../javascript/advanced/special-characters-javascript.md) полный список пробелы и символы конца строки.  
  
 Пример, демонстрирующий способы реализации trim методов см. в разделе [прототипы и наследование прототипов](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `trim`.  
  
```JavaScript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Специальные символы](../../javascript/advanced/special-characters-javascript.md)   
 [Объект String](../../javascript/reference/string-object-javascript.md)   
 [Прокрутки, сдвига и масштабирования примера приложения](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)