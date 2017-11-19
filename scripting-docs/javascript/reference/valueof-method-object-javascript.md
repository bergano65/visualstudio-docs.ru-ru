---
title: "Метод valueOf (Object) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: valueOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: valueOf method
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 677b56fd6fc142ce175b130d2f83291c1ac9535f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-object-javascript"></a>Метод valueOf (Object) (JavaScript)
Возвращает примитивное значение указанного объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.valueOf( )  
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `object` ссылка является внутренней [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объекта.  
  
 `valueOf` Метод определен по-разному для каждого встроенная функция [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объекта.  
  
|Объект|Возвращаемое значение|  
|------------|------------------|  
|Массив|Возвращает экземпляр массива.|  
|Boolean|Логическое значение.|  
|Дата|Значение сохраненное время в миллисекундах с полуночи 1 января 1970 г. UTC.|  
|Функция|Самой функции.|  
|Число|Числовое значение.|  
|Объект|Сам объект. Это значение по умолчанию.|  
|Строка|Строковое значение.|  
  
 **Математические** и `Error` объекты не имеют `valueOf` метод.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **Применяется к**: [объект Array](../../javascript/reference/array-object-javascript.md)&#124; [Логический объект](../../javascript/reference/boolean-object-javascript.md)&#124; [Дата объекта](../../javascript/reference/date-object-javascript.md)&#124; [Функции объекта](../../javascript/reference/function-object-javascript.md)&#124; [Номер объекта](../../javascript/reference/number-object-javascript.md)&#124; [Объекта](../../javascript/reference/object-object-javascript.md)&#124; [Строковый объект](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод toString (Object)](../../javascript/reference/tostring-method-object-javascript.md)