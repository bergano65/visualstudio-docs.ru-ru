---
title: "Функция Debug.Write (JavaScript) | Документы Microsoft"
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
- Write
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- write method [JavaScript]
ms.assetid: fd1cfbb3-46cb-47cc-896c-a70d457dd413
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74aad7a01e0dc166f22173cf193b312e1fd4d804
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="debugwrite-function-javascript"></a>Функция Debug.write (JavaScript)
Отправляет строки в отладчик сценариев.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Debug.write([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>Параметры  
 *str1 str2,..., strN*  
 Необязательно. Строки для отправки в отладчик сценариев.  
  
## <a name="remarks"></a>Примечания  
 `Debug.write` Функция отправляет строки в окне интерпретации отладчика сценариев во время выполнения. Если сценарий не выполняется отладка, `Debug.write` функция не имеет эффекта.  
  
 `Debug.write` Функция практически идентичен `Debug.writeln` функции. Единственным различием является `Debug.writeln` функция отправляет символ перевода строки после отправки строки.  
  
## <a name="example"></a>Пример  
 В этом примере используется `Debug.write` функции, чтобы отобразить значение переменной в окне интерпретации отладчика сценариев.  
  
> [!NOTE]
>  Чтобы выполнить этот пример, необходимо иметь отладчик скриптов и скрипт должен выполняться в режиме отладки.  
>   
>  Internet Explorer 8 включает [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] отладчика. Если вы используете более раннюю версию Internet Explorer, см. раздел [Практическое руководство. Включение и запуск отладки скриптов из Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применяется к**: [объект Debug](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Функция Debug.writeln](../../javascript/reference/debug-writeln-function-javascript.md)