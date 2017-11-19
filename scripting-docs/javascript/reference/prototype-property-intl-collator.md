---
title: "Свойство prototype (Intl.Collator) | Документы Microsoft"
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
ms.assetid: c1bbb523-fb55-4395-b357-34d91cf5bba0
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 696535afde8c497bc98fc2c81a03854d66add6f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-intlcollator"></a>Свойство prototype (Intl.Collator)
Возвращает ссылку на прототип для средства упорядочивания.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
collator.prototype  
```  
  
## <a name="remarks"></a>Примечания  
 `collator` Аргумент — имя средства упорядочивания.  
  
 Чтобы для класса объектов обеспечить базовый набор функциональности, используйте свойство `prototype`. Новые экземпляры объекта "наследуют" поведение прототипа, назначенного этому объекту.  
  
 Например, чтобы добавить метод в объект `Intl.Collator`, возвращающий значение самого большого элемента набора, объявите функцию, добавьте ее в `Intl.Collator.prototype`, а затем используйте ее.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]