---
title: "Свойство prototype (WeakMap) | Документы Microsoft"
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
ms.assetid: d28b8a9b-38c9-443d-9586-7cc74784bd99
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cc1bff0d62f2aeb8d6fb78a0857f287fb34078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-weakmap"></a>Свойство prototype (WeakMap)
Возвращает ссылку на прототип для `WeakMap` объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
weakmap.prototype  
```  
  
## <a name="remarks"></a>Примечания  
 `weakmap` Аргумент является имя `WeakMap` объекта.  
  
 Чтобы для класса объектов обеспечить базовый набор функциональности, используйте свойство `prototype`. Новые экземпляры объекта "наследуют" поведение прототипа, назначенного этому объекту.  
  
 Например, чтобы добавить метод в `WeakMap` объекта, которое возвращает значение самого большого элемента `WeakMap`, объявите функцию, добавьте его в `WeakMap.prototype`, а затем использовать его.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]