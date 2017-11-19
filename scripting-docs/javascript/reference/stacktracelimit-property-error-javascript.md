---
title: "Свойство stackTraceLimit (Error) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Error.stackTraceLimit
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error stack track limit [JavaScript]
- JavaScript error stack
- error stack [JavaScript]
- JavaScript stack trace limit
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9af736ee8b385f93b761f1dfa021c23ee5376292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="stacktracelimit-property-error-javascript"></a>Свойство stackTraceLimit (Error) (JavaScript)
Возвращает или задает лимит трассировки стека, что эквивалентно число ошибок кадров для отображения. Значение по умолчанию равно 10.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## <a name="remarks"></a>Примечания  
 Можно задать `stackTraceLimit` свойство любое положительное значение между 0 и `Infinity`. Если `stackTraceLimit` свойство имеет значение 0, во время, возникает ошибка, отображается не трассировку стека. Если задано отрицательное значение или нечисловое значение, значение преобразуется в 0. Если имеет значение stackTraceLimit `Infinity`, отображается весь стек. В противном случае `ToUint32` используется для преобразования значения.  
  
## <a name="example"></a>Пример  
 Приведенный ниже показано, как задать и затем получить лимит трассировки стека.  
  
```JavaScript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## <a name="requirements"></a>Требования  
 Поддерживается в Internet Explorer 10 и [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] приложения.  
  
 **Применяется к**: [объекта Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Description (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [Свойство Message (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [Свойство Name (Error)](../../javascript/reference/name-property-error-javascript.md)   
 [Свойство stack (Error)](../../javascript/reference/stack-property-error-javascript.md)