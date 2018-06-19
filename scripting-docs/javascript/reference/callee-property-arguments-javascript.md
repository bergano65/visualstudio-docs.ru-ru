---
title: Свойство callee (arguments) (JavaScript) | Документы Microsoft
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
- callee
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- callee property
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33f1c2926d76c0a1f088c8f4222b6f24c004b73b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634064"
---
# <a name="callee-property-arguments-javascript"></a>Свойство callee (arguments) (JavaScript)
Возвращает `Function` объекта выполняется, то есть основной текст указанного `Function` объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
[function.]arguments.callee  
```  
  
## <a name="remarks"></a>Примечания  
 Необязательный *функция* аргумент — имя выполняющегося в данный момент `Function` объекта.  
  
 `callee` Входит свойство **аргументы** объекта, который становится доступным только при выполнении связанной с ним функции.  
  
 Начальное значение `callee` свойство `Function` исполняемый объект. Это позволяет анонимные функции рекурсивно.  
  
## <a name="example"></a>Пример  
  
```JavaScript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Применяется к**: [объект arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Функции объекта](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство caller (Function)](../../javascript/reference/caller-property-function-javascript.md)