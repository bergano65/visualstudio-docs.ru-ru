---
title: "Свойство prototype (Intl.NumberFormat) | Документы Microsoft"
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
ms.assetid: 7f6a7e26-108b-4b32-97c2-7f96b9252c50
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b037ce7476574252966e17fcf64246beeaaea1e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-intlnumberformat"></a>Свойство prototype (Intl.NumberFormat)
Возвращает ссылку на прототип для модуля форматирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
numberFormat.prototype  
```  
  
## <a name="remarks"></a>Примечания  
 `numberFormat` Аргумент — имя модуля форматирования.  
  
 Чтобы для класса объектов обеспечить базовый набор функциональности, используйте свойство `prototype`. Новые экземпляры объекта "наследуют" поведение прототипа, назначенного этому объекту.  
  
 Например, чтобы добавить метод в объект `Intl.NumberFormat`, возвращающий значение самого большого элемента набора, объявите функцию, добавьте ее в `Intl.NumberFormat.prototype`, а затем используйте ее.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]