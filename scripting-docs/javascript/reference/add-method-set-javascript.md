---
title: Метод Add (Set) (JavaScript) | Документы Microsoft
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
ms.assetid: b4eea447-fd5b-4380-978e-1b95f6dbc438
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 287dbfb6480289ed57edc26d41e9900e4a76c27b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633174"
---
# <a name="add-method-set-javascript"></a>Метод add (Set) (JavaScript)
Добавляет новый элемент в набор.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
setObj.add(value)  
```  
  
#### <a name="parameters"></a>Параметры  
 `setObj`  
 Обязательный. Объект `Set`.  
  
 `value`  
 Обязательный. Новый элемент набора `Set`.  
  
## <a name="remarks"></a>Примечания  
 Новый элемент может быть любого типа и должен быть уникальным. При добавлении неуникального элемента в набор `Set` новый элемент не будет добавлен в коллекцию.  
  
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