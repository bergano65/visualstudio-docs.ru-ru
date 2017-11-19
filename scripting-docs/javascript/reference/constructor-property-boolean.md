---
title: "Свойство constructor (Boolean) | Документы Microsoft"
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
ms.assetid: b67ca875-23c6-4687-a5ce-1cdd25d1c923
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 091da5342c4713c8eba646a8bd78c315a6a0fa48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-boolean"></a>Свойство constructor (Boolean)
Указывает функцию, которая создает значение типа Boolean.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
boolean.constructor([[value])  
```  
  
#### <a name="parameters"></a>Параметры  
 `boolean`  
 Имя логического значения.  
  
 `value`  
 Необязательно. Указывает значение типа Boolean. Это может быть цифры 1 или 0, или строки «true» или «false».  
  
## <a name="remarks"></a>Примечания  
 `constructor` Свойство содержит ссылку на функцию, которая создает экземпляры объекта Boolean.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование свойства конструктора.  
  
```JavaScript  
var x = new Boolean("true");  
  
if (x.constructor == Boolean)  
    document.write("Object is a Boolelan.");  
  
// Output:  
// Object is a Boolean.  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]