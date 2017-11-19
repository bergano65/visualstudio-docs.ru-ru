---
title: "Функция Debug.writeln (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: writeln
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: writeIn method
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848760e59632b05605de2d73615a2b025df363da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="debugwriteln-function-javascript"></a>Функция Debug.writeln (JavaScript)
Отправляет строки в отладчик сценариев, за которым следует символ новой строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## <a name="parameters"></a>Параметры  
 *str1 str2,..., strN*  
 Необязательно. Строки для отправки в отладчик сценариев.  
  
## <a name="remarks"></a>Примечания  
 `Debug.writeln` Функция отправляет строки, за которым следует символ новой строки, в окне интерпретации Microsoft Script Debugger во время выполнения. Если сценарий не выполняется отладка, `Debug.writeln` функция не имеет эффекта.  
  
 `Debug.writeln` Функция практически идентичен `Debug.write` функции. Единственным различием является `Debug.write` функция не отправляет символ перевода строки после отправки строки.  
  
## <a name="example"></a>Пример  
 В этом примере используется `Debug.writeln` функции, чтобы отобразить значение переменной в окне интерпретации Microsoft Script Debugger.  
  
> [!NOTE]
>  Чтобы выполнить этот пример, необходимо иметь отладчик скриптов и скрипт должен выполняться в режиме отладки.  
>   
>  Internet Explorer 8 включает [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] отладчика. Если вы используете более раннюю версию Internet Explorer, см. раздел [Практическое руководство. Включение и запуск отладки скриптов из Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применяется к**: [объект Debug](../../javascript/reference/debug-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Функция Debug.write](../../javascript/reference/debug-write-function-javascript.md)