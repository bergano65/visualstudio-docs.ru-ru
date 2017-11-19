---
title: "Свойство constructor (WeakMap) | Документы Microsoft"
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
ms.assetid: 1e3f9333-ce75-4d32-9b14-fbe81fd73dfb
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c7340e1e5eeff9a80e231cf1aa49443adc94e72
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-weakmap"></a>Свойство constructor (WeakMap)
Указывает функцию, которая создает `WeakMap` объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
weakmap.constructor  
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `weakmap` имя `WeakMap` объекта.  
  
 Свойство `constructor` является членом прототипа каждого объекта, который имеет прототип. Сюда относятся все встроенные объекты JavaScript, за исключением объектов `Global` и `Math`. Свойство `constructor` содержит ссылку на функцию, которая создает экземпляры конкретного объекта.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]