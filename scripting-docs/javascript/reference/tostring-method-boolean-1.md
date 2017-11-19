---
title: "(логический) 1 метод toString | Документы Microsoft"
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
ms.assetid: c46b43c0-6946-407a-b0e0-49cba90e226a
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17dd9503e4e09aafca3d153662bf7487538cda3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-boolean-1"></a>(логический) 1 метод toString
Возвращает строковое представление объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
boolean.toString()  
```  
  
## <a name="parameters"></a>Параметры  
 `boolean`  
 Обязательный. Объект, для которого нужно получить строковое представление.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если логическое значение — `true`, возвращает «true». В противном случае возвращает «false».  
  
## <a name="remarks"></a>Примечания  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **toString** метод.  
  
```JavaScript  
var s = new Boolean(0);  
document.write(s.toString());  
  
// Output: false;  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]