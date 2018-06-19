---
title: Свойство prototype (Intl.DateTimeFormat) | Документы Microsoft
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
ms.assetid: e1e693ff-1775-407e-b655-18a60d238ded
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64dff17e4aaf62940f4c9c5f8b422fcbceb7212a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638614"
---
# <a name="prototype-property-intldatetimeformat"></a>Свойство prototype (Intl.DateTimeFormat)
Возвращает ссылку на прототип для модуля форматирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
dateTimeFormat.prototype  
```  
  
## <a name="remarks"></a>Примечания  
 `dateTimeFormat` Аргумент — имя модуля форматирования.  
  
 Чтобы для класса объектов обеспечить базовый набор функциональности, используйте свойство `prototype`. Новые экземпляры объекта "наследуют" поведение прототипа, назначенного этому объекту.  
  
 Например, чтобы добавить метод в объект `Intl.DateTimeFormat`, возвращающий значение самого большого элемента набора, объявите функцию, добавьте ее в `Intl.DateTimeFormat.prototype`, а затем используйте ее.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]