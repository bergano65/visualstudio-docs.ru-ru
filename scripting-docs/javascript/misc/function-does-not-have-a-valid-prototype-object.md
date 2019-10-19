---
title: Функция не имеет допустимого объекта прототипа | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb3cffa4bffd616560aa95ace4ad82a4368ebbd5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574603"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Функция не имеет допустимого объекта прототипа
Предпринята попытка использовать **instanceof** для определения того, был ли объект производным от определенного класса функции, но свойство `prototype` объекта было переопределено как `null` или тип внешнего объекта (как недопустимые [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объекты). Внешним объектом может быть объект из объектной модели узла (например, документ или объект окна Internet Explorer) или внешний COM-объект.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что свойство `prototype` функции ссылается на допустимый объект [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Объект функции](../../javascript/reference/function-object-javascript.md)    
 [Свойство prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)