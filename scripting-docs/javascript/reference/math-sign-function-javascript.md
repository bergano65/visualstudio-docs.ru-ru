---
title: "Функция Math.Sign (JavaScript) | Документы Microsoft"
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
ms.assetid: 8b462020-ceff-4947-8dd1-c78e6aff8d98
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cae32118f2265e02c67592facff8e49e8edd633
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="mathsign-function-javascript"></a>Функция Math.sign (JavaScript)
Возвращает знак числа, указывающий, является ли число положительным, отрицательным или равным 0.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Math.sign(number)  
```  
  
## <a name="remarks"></a>Примечания  
 Обязательный аргумент `number` является числовым выражением, для которого требуется знак.  
  
 Возвращается одно из следующих значений:  
  
-   `NaN`, если `number` равно `NaN`.  
  
-   -0, если `number` — - 0.  
  
-   +0, если `number` равно +0.  
  
-   значение -1, если `number` является отрицательным и не - 0.  
  
-   +1, если `number` является положительным числом и не равно +0.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]