---
title: "Метод toLocaleLowerCase (String) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- toLocaleLowerCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleLowerCase method
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 642ced387e0d3b4cf763767ec147d6160ed7d36b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalelowercase-method-string-javascript"></a>Метод toLocaleLowerCase (String) (JavaScript)
Преобразует все буквенные символы в нижний регистр с учетом текущего языкового стандарта хост-среды.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `stringVar` ссылка `String` или строковый литерал.  
  
 `toLocaleLowerCase` Метод преобразует символы в строке с учетом текущего языкового стандарта хост-среды. В большинстве случаев результат зависит от того как результат `toLowerCase` метод. Результаты отличаются, если правила языка противоречит регулярного сопоставление регистра Юникода.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Применяется к**: [строковый объект](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод toLocaleUpperCase (String)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [Метод toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)