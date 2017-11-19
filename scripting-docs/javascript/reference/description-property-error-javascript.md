---
title: "Свойство Description (Error) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Description
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error handling, error description
- Description property
- errors, description
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6135951fdf65698ed48b9bbacdcc55c1aac22d41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="description-property-error-javascript"></a>Свойство description (Error) (JavaScript)
Возвращает или задает строку описания, связанный с определенной ошибки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## <a name="parameters"></a>Параметры  
 *object*  
 Обязательный. Любой экземпляр `Error` объекта.  
  
 `stringExpression`  
 Необязательно. Строковое выражение, содержащее описание ошибки.  
  
## <a name="remarks"></a>Примечания  
 **Описание** свойство содержит строку сообщения ошибки, связанные с определенной ошибки. Значение этого свойства используется для предупреждения пользователя об ошибке.  
  
 **Описание** и **сообщение** свойства предоставляют те же функциональные возможности; **описание** свойство обеспечивает обратную совместимость;  **сообщение** свойства соответствует стандарту ECMA.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **описание** свойство.  
  
```JavaScript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Применяется к**: [объекта Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Number (Error)](../../javascript/reference/number-property-error-javascript.md)   
 [Свойство Message (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [Свойство name (Error)](../../javascript/reference/name-property-error-javascript.md)