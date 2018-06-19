---
title: Функция Symbol.for (JavaScript) | Документы Microsoft
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
ms.assetid: 27db15f3-9108-4892-8f89-e84031729cb6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b7e47c00fbaa321d71a3eeba79e523eee719fb2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639664"
---
# <a name="symbolfor-function-javascript"></a>Функция Symbol.for (JavaScript)
Возвращает символ для указанного ключа или, если этот ключ отсутствует, создает новый объект Symbol с новым ключом.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Symbol.for(key);  
```  
  
#### <a name="parameters"></a>Параметры  
 `key`  
 Обязательный. Ключ для символа, который также используется в качестве описания.  
  
## <a name="remarks"></a>Примечания  
 Этот метод осуществляет поиск символа в реестре глобальных символов. При сериализации символов в виде строк используйте реестр глобальных символов, чтобы убедиться, что строки сопоставляются с правильными символами во всех случаях.  
  
## <a name="example"></a>Пример  
  
```JavaScript  
var sym = Symbol.for("desc");  
  
console.log(sym.toString());  
  
// Two different object references.  
console.log(Symbol("symbol") === Symbol.for("symbol");)  
// Single object reference.   
console.log(Symbol.for("symbol") === Symbol.for("symbol");)  
  
// Output:  
// Symbol(desc);  
// false  
// true  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]