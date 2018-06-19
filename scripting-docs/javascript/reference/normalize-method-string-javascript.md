---
title: Метод normalize (String) (JavaScript) | Документы Microsoft
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
ms.assetid: d50077c1-b5fa-4e7a-9c9d-dc66cfc423ac
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aece38339ea1ce8924f404938b2d35d07504d539
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638744"
---
# <a name="normalize-method-string-javascript"></a>Метод normalize (String) (JavaScript)
Возвращает форму нормализации Юникода для указанной строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
stringObj.normalize([form]);  
```  
  
#### <a name="parameters"></a>Параметры  
 `stringObj`  
 Обязательный. Строковый объект для проверки.  
  
 `form`  
 Необязательно. Значение формы нормализации Юникода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Форма нормализации Юникода для указанной строки.  
  
## <a name="exceptions"></a>Исключения  
 Если `form` представляет собой неподдерживаемое значение, вызывается исключение `RangeError`.  
  
## <a name="remarks"></a>Примечания  
 Если `stringObj` не является строкой, он будет преобразован в строку до того, как метод попытается вернуть форму нормализации Юникода для строки.  
  
 `form`должно быть значение формы нормализации Юникода «NFC», «NFD», «NFKC» или «NFKD», соответствующий значения, указанные для [Unicode Standard Annex #15](http://www.unicode.org/reports/tr15/). Значение по умолчанию для `form` — NFC.  
  
## <a name="example"></a>Пример  
 В следующих примерах кода показано использование метода `normalize`.  
  
```JavaScript  
// ANGSTORM SIGN and LATIN CAPITAL A WITH RING ABOVE is canonically equivalent  
"\u212b".normalize("NFC") === "\u00c5";  
  
// Decomposed, ANGSTOM SIGN is LATIN CAPITAL A followed by COMBINING RING ABOVE  
"\u212b".normalize("NFD") === "\u0041\u030a"  
  
// Normalization Form C will combine the result back into the precombined character  
"\u0041\u030a".normalize("NFC") === "\u00c5"  
  
// LATIN SMALL LIGATURE FI is compatibility equivalent with LATIN SMALL LETTER F followed by  
// LATIN SMALL LETTER I.  
"\ufb01".normalize("NFKD") === "fi";  
  
// Same mapping in NFKC  
"\ufb01".normalize("NFKC") === "fi";  
  
// NFKC will not recombine compatibility characters.  
"fi".normalize("NFKC") === "fi";  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]