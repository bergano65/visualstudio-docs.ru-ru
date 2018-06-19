---
title: Объект WeakSet (JavaScript) | Документы Microsoft
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
ms.assetid: f97e6e7c-d678-4e32-978e-d949a7cafa3a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e42849c03f698d6ed5f8b0e28725c85555a74d2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641604"
---
# <a name="weakset-object-javascript"></a>Объект WeakSet (JavaScript)
Коллекция уникальных объектов, которые могут принадлежать к любому типу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
setObj = new WeakSet()  
```  
  
## <a name="remarks"></a>Примечания  
 При добавлении неуникального объекта в `WeakSet` новый объект не будет добавлен в коллекцию.  
  
 В отличие от `Set`, в коллекцию могут быть добавлены только объекты. Произвольные значения не могут быть добавлены в коллекцию.  
  
 В `WeakSet` объект ссылки на объекты в наборе удерживаются «слабо». Это означает, что `WeakSet` не будет предотвращать сборку мусора в объектах. При отсутствии ссылок (отличных от `WeakSet`) на объекты сборщик мусора может собирать объекты.  
  
 `WeakSet` (или `WeakMap`) может оказаться полезным в некоторых сценариях, где применяется кэширование объектов или метаданных объекта. Например, метаданные для нерасширяемых объектов могут храниться в `WeakSet` или вы можете создать кэш изображений пользователя с помощью `WeakSet`.  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены свойства объекта `WeakSet`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|constructor|Указывает функцию, которая создает набор.|  
|prototype|Возвращает ссылку на прототип для набора.|  
  
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `WeakSet`.  
  
|Метод|Описание|  
|------------|-----------------|  
|add|Добавляет элемент в набор.|  
|delete|Удаляет указанный элемент из набора.|  
|has|Возвращает `true`, если набор содержит указанный элемент.|  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как добавить элементы в набор, а затем проверить, что они были добавлены.  
  
```JavaScript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]