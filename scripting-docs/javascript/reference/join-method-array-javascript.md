---
title: Метод Join (Array) (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- join
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Join method
- concatenating strings, join method
- arrays [Visual Studio], joining
ms.assetid: 20f8fde1-014b-488e-9008-464a86e6b21f
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4591b12b3556384fef3e367d20cf9545d2f3dedd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637614"
---
# <a name="join-method-array-javascript"></a>Метод join (Array) (JavaScript)
Добавляет все элементы массива, разделенных указанной строкой-разделителем.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
arrayObj.join([separator])   
```  
  
## <a name="parameters"></a>Параметры  
 `arrayObj`  
 Обязательный. Объект `Array`.  
  
 `separator`  
 Необязательно. Строка, используемая для разделения одного элемента массива от следующего в результате `String`. Если не указано, элементы массива разделяются запятыми.  
  
## <a name="remarks"></a>Примечания  
 Если любой элемент массива **не определено** или `null`, он рассматривается как пустая строка.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **соединения** метод.  
  
```JavaScript  
var a, b;  
a = new Array(0,1,2,3,4);  
b = a.join("-");  
document.write(b);  
  
// Output:  
// 0-1-2-3-4  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Объект String](../../javascript/reference/string-object-javascript.md)