---
title: "Метод toLocaleUpperCase (String) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleUpperCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleUpperCase method
ms.assetid: e927adb6-475e-44b2-91f7-cedda10a39b0
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07a89560dde0319598da30fc3451524112b99eac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="tolocaleuppercase-method-string-javascript"></a>Метод toLocaleUpperCase (String) (JavaScript)
Возвращает строку, в которой все буквенные символы были текущего языкового стандарта преобразованное в верхний регистр с учетом узел среды.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
stringVar.toLocaleUpperCase( )  
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `stringVar` ссылка `String` или строковый литерал.  
  
 `toLocaleUpperCase` Метод преобразует символы в строке с учетом текущего языкового стандарта хост-среды. В большинстве случаев результат зависит от того как результат `toUpperCase` метод. Результаты отличаются, если правила языка противоречит регулярного сопоставление регистра Юникода.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Применяется к**: [строковый объект](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод toLocaleLowerCase (String)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [Метод toUpperCase (String)](../../javascript/reference/touppercase-method-string-javascript.md)