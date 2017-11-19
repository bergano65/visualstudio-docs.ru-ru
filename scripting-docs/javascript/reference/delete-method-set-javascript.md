---
title: "Метод Delete (Set) (JavaScript) | Документы Microsoft"
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
ms.assetid: 052c409e-10c9-49f2-955d-5ad7e31c14f3
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72762b93c6996fd72bd035c5d653f0e85f4ffd33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="delete-method-set-javascript"></a>Метод delete (Set) (JavaScript)
Удаляет указанный элемент из набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
setObj.delete(value)  
```  
  
#### <a name="parameters"></a>Параметры  
 `setObj`  
 Обязательный. Объект `Set`.  
  
 `value`  
 Обязательный. Подлежащий удалению элемент.  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 `true`, если элемент был удален.  
  
## <a name="example"></a>Пример  
 Следующий пример демонстрирует добавление членов в `Set` , а затем удалите один из них.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
s.delete("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776,  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]