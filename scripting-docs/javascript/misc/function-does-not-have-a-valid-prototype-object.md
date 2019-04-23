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
ms.openlocfilehash: 413f73a53a6d4f698219139a87c449be4c155831
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60038683"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Функция не имеет допустимого объекта прототипа
Вы попытались использовать **instanceof** для определения, если объект, производный от класса определенной функции, но переопределен объекта `prototype` свойство как `null`, или тип внешнего объекта (оба не является допустимым [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объектов). Внешний объект может быть объект из объектной модели узла (например, документ Internet Explorer или объект окна) или внешним COM-объектом.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, функции `prototype` свойство ссылается на допустимый [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объекта.  
  
## <a name="see-also"></a>См. также  
 [Объект функции](../../javascript/reference/function-object-javascript.md)   
 [Свойство prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)