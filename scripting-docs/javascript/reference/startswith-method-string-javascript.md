---
title: "Метод startsWith (String) (JavaScript) | Документы Microsoft"
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
ms.assetid: 871def4a-0f96-4675-b6ff-2349f4996511
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74970a9a3bfe280e91f2df39340732eda8664142
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="startswith-method-string-javascript"></a>Метод startsWith (String) (JavaScript)
Возвращает значение, показывающее, начинается ли строка или подстрока с другой указанной строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
  
stringObj.startsWith(str, [, position]);  
```  
  
#### <a name="parameters"></a>Параметры  
 `stringObj`  
 Обязательный. Объект string для поиска.  
  
 `str`  
 Обязательный. Строка поиска.  
  
 `position`  
 Необязательно. Позиция первого символа для поиска в объекте string, начинающемся с 0.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если строка в позиции `position` начинается с искомой строки, метод `startsWith` возвращает значение `true`; в противном случае возвращается значение `false`.  
  
## <a name="exceptions"></a>Исключения  
 Если `str` представляет собой `RegExp`, возникает ошибка `TypeError`.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]