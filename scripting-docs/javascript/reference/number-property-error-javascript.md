---
title: число свойств (Error) (JavaScript) | Документы Microsoft
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
- Number
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Number property
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbc229e7d0572e1a3dbed056b344da7ff9ce7292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639104"
---
# <a name="number-property-error-javascript"></a>Свойство number (Error) (JavaScript)
Возвращает или задает числовое значение, связанное с определенной ошибкой. `Error` Объекта по умолчанию свойство имеет **номер**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## <a name="parameters"></a>Параметры  
 *Объект*  
 Любой экземпляр `Error` объекта.  
  
 *номер ошибки*  
 Целое число, представляющее ошибку.  
  
## <a name="remarks"></a>Примечания  
 Номер ошибки представляет собой 32-разрядное значение. Старшие 16-разрядное — это код устройства, а младшие разряды — код ошибки. Чтобы определить код ошибки, используйте `&` (побитовое и) оператор, чтобы объединить свойство number с шестнадцатеричным числом `0xFFFF`.  
  
## <a name="example"></a>Пример  
 Следующий пример приводит к возникновению исключения исключение и отображает код ошибки, который является производным от номер ошибки.  
  
```JavaScript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## <a name="example"></a>Пример  
 Результат выполнения этого кода выглядит следующим образом.  
  
```JavaScript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Применяется к**: [объекта Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Description (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [Свойство Message (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [Свойство name (Error)](../../javascript/reference/name-property-error-javascript.md)