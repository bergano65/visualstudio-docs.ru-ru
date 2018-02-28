---
title: "окна отладчика оператор (JavaScript) | Документы Microsoft"
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
- debugger_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- debugger statement
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e64e860cebd065f357857484e932b4aea3f05ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="debugger-statement-javascript"></a>Оператор debugger (JavaScript)
Приостанавливает выполнение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
debugger  
```  
  
## <a name="remarks"></a>Примечания  
 Можно поместить `debugger` инструкций в любом месте процедуры для приостановки выполнения. С помощью `debugger` инструкция похожа на задание точки останова в коде.  
  
 `debugger` Оператор приостанавливает выполнение, но не закрывает все файлы и не удаляет переменные.  
  
> [!NOTE]
>  `debugger` Инструкция действует только скрипт выполняется отладка.  
  
## <a name="example"></a>Пример  
 В этом примере используется `debugger` инструкции для приостановки выполнения на каждом шаге цикла `for` цикла.  
  
> [!NOTE]
>  Чтобы выполнить этот пример, необходимо иметь отладчик скриптов и скрипт должен выполняться в режиме отладки.  
>   
>  Internet Explorer 8 включает [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] отладчика. Если вы используете более раннюю версию Internet Explorer, см. раздел [Практическое руководство. Включение и запуск отладки скриптов из Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Операторы JavaScript](../../javascript/reference/javascript-statements.md)   
 [Условная компиляция](../../javascript/advanced/conditional-compilation-javascript.md)