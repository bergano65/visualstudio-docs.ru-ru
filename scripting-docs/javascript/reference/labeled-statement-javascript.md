---
title: "Оператор (JavaScript) с меткой | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- labeled_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- continue statement
- labeled statement
- identifiers, statements
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd72b15d3fc9083ca127a48981c0cd0a7ee56b6c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="labeled-statement-javascript"></a>Оператор с идентификатором (JavaScript)
Предоставляет идентификатор для оператора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      label :  
   statements   
```  
  
## <a name="parameters"></a>Параметры  
 *Метка*  
 Обязательный. Уникальный идентификатор, используемый при обращении к оператору с меткой.  
  
 `statements`  
 Необязательно. Один или несколько операторов, связанные с *метка*.  
  
## <a name="remarks"></a>Примечания  
 Метки используются **разрыв** и **Продолжить** инструкции, чтобы указать инструкции, к которому **разрыв** и **Продолжить** применения.  
  
## <a name="example"></a>Пример  
 В следующем коде **Продолжить** Инструкция ссылается на **для** цикл, который предшествует `Inner:` инструкции. Когда `j` 24, **Продолжить** инструкция вызывает, **для** переход к следующей итерации цикла. Значения от 21 до 23 и 25 до 30 печати в каждой строке.  
  
```JavaScript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор break](../../javascript/reference/break-statement-javascript.md)   
 [Оператор continue](../../javascript/reference/continue-statement-javascript.md)