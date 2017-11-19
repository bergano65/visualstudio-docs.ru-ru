---
title: "Метод valueOf (String) | Документы Microsoft"
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
ms.assetid: dfb55e6b-e38f-4b49-8196-9693f87126a4
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15fe978fb0628c046f369f565bb464353f1e6812
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-string"></a>Метод valueOf (String)
Возвращает строку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
string.valueOf()  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не имеет параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает строковое значение.  
  
## <a name="remarks"></a>Примечания  
 В следующем примере объект string является таким же, как возвращаемое значение.  
  
```JavaScript  
var str = "every good boy does fine";  
var strStr = str.valueOf();  
  
if (str === strStr)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]