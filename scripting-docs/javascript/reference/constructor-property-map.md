---
title: "Свойство constructor (Map) | Документы Microsoft"
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
ms.assetid: a90d6a29-bd64-4e01-8d2f-988b7e3e4a24
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7050f4a7eab149862c08ea755361b5bd0d297299
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-map"></a>Свойство constructor (Map)
Указывает функцию, которая создает карту.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
map.constructor  
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `map` имя сопоставления.  
  
 Свойство `constructor` является членом прототипа каждого объекта, который имеет прототип. Сюда относятся все встроенные объекты JavaScript, за исключением объектов `Global` и `Math`. Свойство `constructor` содержит ссылку на функцию, которая создает экземпляры конкретного объекта.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]