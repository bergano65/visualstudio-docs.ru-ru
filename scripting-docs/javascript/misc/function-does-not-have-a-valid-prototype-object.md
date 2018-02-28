---
title: "Функция не имеет допустимого объекта прототипа | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4e2cbf198a452cd61f1355682ea3041436d2a27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Функция не имеет допустимого объекта прототипа
Предпринята попытка использования **instanceof** для определения, если объект, производный от класса определенной функции, но переопределен объекта `prototype` свойство как `null`, или тип внешнего объекта (оба не является допустимым [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объектов). Внешний объект может быть объект из объектной модели узла (например, документ Internet Explorer или объект окна) или внешним COM-объектом.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Убедитесь, функция `prototype` свойство ссылается на допустимый [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объекта.  
  
## <a name="see-also"></a>См. также  
 [Объект функции](../../javascript/reference/function-object-javascript.md)   
 [Свойство prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)