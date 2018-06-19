---
title: Свойство Stack (Error) (JavaScript) | Документы Microsoft
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
- Error.stack
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript error stack
- error stack [JavaScript]
ms.assetid: 1dc21fdd-853c-4664-bf1c-24eb1f6f2daf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14e4a2537b1543b7e8d9727afdeb8ea5dee61bbc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641144"
---
# <a name="stack-property-error-javascript"></a>Свойство stack (Error) (JavaScript)
Получает или задает стек ошибок в качестве строки, содержащей кадры трассировки стека.   
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.stack   
```  
  
## <a name="remarks"></a>Примечания  
 Свойству `stack` задается значение `undefined`, если ошибка сконструирована, и свойство получает сведения о трассировке при возникновении ошибки. Если ошибка возникает несколько раз, то значение свойства `stack` обновляется каждый раз при ее возникновении.   
  
 Кадры стека отображаются в следующем формате: **в FunctionName (\<полное доменное имя или URL-адрес >:\<номер строки >:\<номер столбца >)**  
  
 При создании собственного объекта Error и присвоении значения трассировке стека это значение не будет перезаписано при возникновении ошибки.  
  
 Свойство `stack` не отображает встраиваемые функции в кадрах. Оно показывает только физические стеки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как получить стек при перехвате ошибки.  
  
```JavaScript  
try  
    {  
        var x = y.name;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как задать, а затем получить стек.  
  
```JavaScript  
try  
    {  
        var err = Error("my error");  
        err.stack = "my stack trace";  
        throw err;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]  
  
 **Применяется к**: [объекта Error](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Description (Error)](../../javascript/reference/description-property-error-javascript.md)   
 [Свойство Message (Error)](../../javascript/reference/message-property-error-javascript.md)   
 [Свойство Name (Error)](../../javascript/reference/name-property-error-javascript.md)   
 [Свойство stackTraceLimit (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)