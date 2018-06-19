---
title: Свойство constructor (WeakSet) | Документы Microsoft
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
ms.assetid: 234e7104-9b78-4bfa-8f77-2bc44a570928
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5519c37f459e8236c6ed482b181799076832c50b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636134"
---
# <a name="constructor-property-weakset"></a>Свойство constructor (WeakSet)
Указывает функцию, которая создает `WeakSet`.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
weakset.constructor  
```  
  
## <a name="remarks"></a>Примечания  
 Обязательный `weakset` — имя набора данных.  
  
 Свойство `constructor` является членом прототипа каждого объекта, который имеет прототип. Сюда относятся все встроенные объекты JavaScript, за исключением объектов `Global` и `Math`. Свойство `constructor` содержит ссылку на функцию, которая создает экземпляры конкретного объекта.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]