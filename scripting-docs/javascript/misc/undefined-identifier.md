---
title: Неопределенный идентификатор | Документация Майкрософт
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
- VS.WebClient.Help.SCRIPT5009
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8c8000d9-dd14-487e-922d-98430024a0f6
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f54117dc6d169d11498f15d034fa584fc2e9f64b
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346141"
---
# <a name="undefined-identifier"></a>Неопределенный идентификатор
Была предпринята попытка использовать идентификатор, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] компилятор не распознает. Неопределенное значение возвращается при каждом выполнении:  
  
-   переменную, которая не существует,  
  
-   переменную, которая объявлен, но никогда не было присвоено значение,  
  
-   свойство объекта, которое не существует.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Объявите переменную с **var** инструкции (как в `var` x;).  
  
## <a name="see-also"></a>См. также  
 [Переменные](../../javascript/variables-javascript.md)   
 [Область действия переменных](../../javascript/advanced/variable-scope-javascript.md)