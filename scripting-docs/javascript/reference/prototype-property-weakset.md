---
title: "Свойство prototype (WeakSet) | Документы Microsoft"
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
ms.assetid: 950e15a2-2f56-4cb9-8e48-020efd97f938
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c66c7854a83dcf3128025350a7fcdd17f4dfaf5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-weakset"></a>Свойство prototype (WeakSet)
Возвращает ссылку на прототип для `WeakSet`.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
weakset.prototype  
```  
  
## <a name="remarks"></a>Примечания  
 Аргумент `weakset` является именем набора.  
  
 Чтобы для класса объектов обеспечить базовый набор функциональности, используйте свойство `prototype`. Новые экземпляры объекта "наследуют" поведение прототипа, назначенного этому объекту.  
  
 Например, чтобы добавить метод в объект `WeakSet`, возвращающий значение самого большого элемента набора, объявите функцию, добавьте ее в `WeakSet.prototype`, а затем используйте ее.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]