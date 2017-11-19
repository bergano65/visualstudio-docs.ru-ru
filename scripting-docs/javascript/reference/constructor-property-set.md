---
title: "Свойство constructor (Set) | Документы Microsoft"
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
ms.assetid: f350b7eb-8994-40bf-9011-f8b20fcef34f
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea9af6d60c2ae8bc8a383c4cebbf0955e183895e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-set"></a>Свойство constructor (Set)
Указывает функцию, которая создает набор.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
set.constructor  
```  
  
## <a name="remarks"></a>Примечания  
 Обязательный `set` — имя набора данных.  
  
 Свойство `constructor` является членом прототипа каждого объекта, который имеет прототип. Сюда относятся все встроенные объекты JavaScript, за исключением объектов `Global` и `Math`. Свойство `constructor` содержит ссылку на функцию, которая создает экземпляры конкретного объекта.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]