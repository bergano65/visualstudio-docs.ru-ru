---
title: "Свойство CALLER (Function) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: caller
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- caller property
- function calls, functions that are executing
ms.assetid: ae210853-7160-4102-9cfd-ab489f180ce1
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c6eef1b8304612c2ed16a4cc389bf3b2a28b70f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="caller-property-function-javascript"></a>Свойство caller (Function) (JavaScript)
Возвращает функцию, которая вызвала текущую функцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
functionName.caller  
```  
  
## <a name="remarks"></a>Примечания  
 `functionName` Объекта является имя любой выполнение функции.  
  
 `caller` Определяется свойство для функции только во время исполнения функции. Если функция вызывается от верхнего уровня [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] программы, `caller` содержит `null`.  
  
 Если `caller` свойство используется в контексте строк, результат будет таким же, как `functionName`.`toString`, то есть отображается декомпилированный текст функции.  
  
 В следующем примере показано применение свойства `caller`.  
  
```JavaScript  
function CallLevel(){  
   if (CallLevel.caller == null)  
      return("CallLevel was called from the top level.");  
   else  
      return("CallLevel was called by another function.");  
}  
  
document.write(CallLevel());  
  
// Output: CallLevel was called from the top level.  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор function](../../javascript/reference/function-statement-javascript.md)