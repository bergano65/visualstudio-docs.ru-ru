---
title: "Свойство Message (Error) (JavaScript) | Документы Microsoft"
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
- message
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Message property
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9dbd2db6c6d31dc48d90c3b07d2388eacf73ae7a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="message-property-error-javascript"></a>Свойство message (Error) (JavaScript)
Возвращает строку сообщения об ошибке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
errorObj.message  
```  
  
## <a name="parameters"></a>Параметры  
 `errorObj`  
 Обязательный. Экземпляр `Error` объекта.  
  
## <a name="remarks"></a>Примечания  
 `message` Свойство возвращает строку, содержащую сообщение об ошибке, связанное с определенной ошибкой.  
  
 `description` И `message` свойства предоставляют те же функциональные возможности. `description` Свойство обеспечивает обратную совместимость; `message` свойства соответствует стандарту ECMA.  
  
## <a name="example"></a>Пример  
 Следующий пример приводит к возникновению исключения TypeError и отображает имя и текст ошибки.  
  
```JavaScript  
try  
{  
    // Cause an error.  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## <a name="example"></a>Пример  
 Результат выполнения этого кода выглядит следующим образом.  
  
```JavaScript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Применяется к**: [объекта Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Description (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [Свойство name (Error)](../../javascript/reference/name-property-error-javascript.md)