---
title: Функция не имеет допустимого объекта прототипа | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4e2cbf198a452cd61f1355682ea3041436d2a27
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346700"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Функция не имеет допустимого объекта прототипа
Вы попытались использовать **instanceof** для определения, если объект, производный от класса определенной функции, но переопределен объекта `prototype` свойство как `null`, или тип внешнего объекта (оба не является допустимым [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объектов). Внешний объект может быть объект из объектной модели узла (например, документ Internet Explorer или объект окна) или внешним COM-объектом.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Убедитесь, функции `prototype` свойство ссылается на допустимый [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объекта.  
  
## <a name="see-also"></a>См. также  
 [Объект функции](../../javascript/reference/function-object-javascript.md)   
 [Свойство prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)