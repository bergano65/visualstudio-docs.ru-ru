---
title: "Объект SET (JavaScript) | Документы Microsoft"
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
- Set
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4a4dd749-2a76-44fb-9cb0-a3ef317f75fb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5134ec09c9a8642499212af9dd5fd44de0068adc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="set-object-javascript"></a>Объект Set (JavaScript)
Коллекция уникальных значений, которые могут принадлежать к любому типу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
setObj = new Set()     
```  
  
## <a name="remarks"></a>Примечания  
 При попытке добавить неуникальное значение `Set`, новое значение не будет добавляться в коллекцию.  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены свойства объекта `Set`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Конструктор](../../javascript/reference/constructor-property-set.md)|Указывает функцию, которая создает набор.|  
|[прототип](../../javascript/reference/prototype-property-set.md)|Возвращает ссылку на прототип для набора.|  
|[size](../../javascript/reference/size-property-set-javascript.md)|Возвращает количество элементов в наборе.|  
  
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `Set`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[add](../../javascript/reference/add-method-set-javascript.md)|Добавляет элемент в набор.|  
|[clear](../../javascript/reference/clear-method-set-javascript.md)|Удаляет все элементы из набора.|  
|[удалить](../../javascript/reference/delete-method-set-javascript.md)|Удаляет указанный элемент из набора.|  
|[по каждому элементу](../../javascript/reference/foreach-method-set-javascript.md)|Выполняет указанное действие для каждого элемента в наборе.|  
|[имеет](../../javascript/reference/has-method-set-javascript.md)|Возвращает `true`, если набор содержит указанный элемент.|  
|[toString](../../javascript/reference/tostring-method-set-javascript.md)|Возвращает строковое представление набора.|  
|[valueOf](../../javascript/reference/valueof-method-set-javascript.md)|Возвращает примитивное значение указанного объекта.|  
  
## <a name="example"></a>Пример  
 В следующем примере показано добавление членов в набор и затем извлечение их.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]