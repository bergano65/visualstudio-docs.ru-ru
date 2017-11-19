---
title: "Метод includes (String) (JavaScript) | Документы Microsoft"
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
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 848143b64d3e32452aea41f08b6f5c57879d3e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="includes-method-string-javascript"></a>Метод includes (String) (JavaScript)
Возвращает логическое значение, указывающее, содержится ли переданная строка в объекте String.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### <a name="parameters"></a>Параметры  
 `stringObj`  
 Обязательный. Строковый объект для проверки.  
  
 `substring`  
 Обязательный. Строка для проверки.  
  
 `position`  
 Необязательно. Позиция первого символа для проверки в объекте string, начинающемся с 0.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если переданная строка содержится в объекте string, метод `includes` возвращает `true`, а если нет, то `false`.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="example"></a>Пример  
  
```JavaScript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]