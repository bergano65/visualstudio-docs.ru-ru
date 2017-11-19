---
title: "Метод toString (Error) | Документы Microsoft"
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
ms.assetid: 5d6d9712-c06d-4b31-9bc9-e46f6bb5cd38
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d774ff8c0f5338f4178b2262bf8ac8cadc074453
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-error"></a>Метод toString (Error)
Возвращает строковое представление ошибки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
error.toString()  
```  
  
## <a name="parameters"></a>Параметры  
 `date`  
 Обязательный. Ошибка для представления в виде строки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает «ошибка: "плюс сообщение об ошибке.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование `toString` метода с ошибкой.  
  
```JavaScript  
var myError = new Error();  
myError.message = "My Error";  
var errorString = myError.toString();  
document.write(errorString);  
  
// Output: Error: My Error  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]