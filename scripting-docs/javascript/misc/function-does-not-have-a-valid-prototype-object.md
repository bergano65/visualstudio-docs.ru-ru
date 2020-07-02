---
title: Функция не имеет допустимого объекта прототипа | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: ca6f13620bb486cf1663bd5bef9a9a93b2c8a480
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817363"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Функция не имеет допустимого объекта прототипа
Вы попытались использовать **instanceof** , чтобы определить, является ли объект производным от определенного класса функции, но свойство объекта было переопределено `prototype` как либо либо `null` тип внешнего объекта (как недопустимые [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объекты). Внешним объектом может быть объект из объектной модели узла (например, документ или объект окна Internet Explorer) или внешний COM-объект.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что `prototype` свойство функции ссылается на допустимый [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объект.  
  
## <a name="see-also"></a>См. также  
 [Объект функции](../../javascript/reference/function-object-javascript.md)   
 [Свойство prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)