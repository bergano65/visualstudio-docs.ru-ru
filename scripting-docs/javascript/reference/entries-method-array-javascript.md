---
title: Метод entries (Array) (JavaScript) | Документы Microsoft
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
ms.assetid: 9bc46afb-74d2-4f99-8c95-f46475acf21d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff1e32ba0782d637ea1418daf5b3a56203d7e34b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636324"
---
# <a name="entries-method-array-javascript"></a>Метод entries (Array) (JavaScript)
Возвращает итератор, который возвращает пары "ключ-значение" массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
arrayObj.entries();  
```  
  
#### <a name="parameters"></a>Параметры  
 `arrayObj`  
 Обязательный. Объект массива.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как получить пары "ключ-значение" массива.  
  
```JavaScript  
var entries = ["a", "b", "c"].entries();  
// entries.next().value == [0, "a"]  
// entries.next().value == [1, "b"]  
// entries.next().value == [2, "c"]   
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]