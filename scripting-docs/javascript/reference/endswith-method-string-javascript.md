---
title: Метод endsWith (String) (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c7d836e3-bc43-4d1b-be60-0a93beb8b7a2
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc6d57d501f0f100f069522e4b51666918168fa0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636344"
---
# <a name="endswith-method-string-javascript"></a>Метод endsWith (String) (JavaScript)
Возвращает значение, показывающее, заканчивается ли строка или подстрока другой указанной строкой.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
  
stringObj.endsWith(str, [, position]);  
```  
  
#### <a name="parameters"></a>Параметры  
 `stringObj`  
 Обязательный. Объект string для поиска.  
  
 `str`  
 Обязательный. Строка поиска.  
  
 `position`  
 Необязательно. Позиция первого символа для поиска в объекте string, начинающемся с 0.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если строка в позиции `position` заканчивается искомой строкой, метод `endsWith` возвращает значение `true`; в противном случае возвращается значение `false`.  
  
## <a name="exceptions"></a>Исключения  
 Если `str` представляет собой `RegExp`, возникает ошибка `TypeError`.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]