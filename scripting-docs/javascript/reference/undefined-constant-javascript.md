---
title: "не определено константы (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: undefined
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: undefined property
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ba7fa8b160e4f5d954c8d6545da5fae41c2f74b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="undefined-constant-javascript"></a>Константа undefined (JavaScript)
Значение, которое никогда не была определена, например переменную, не был инициализирован.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
undefined  
```  
  
## <a name="remarks"></a>Примечания  
 `undefined` Константой входит в состав `Global` объекта и становится доступным при инициализации обработчика сценариев. Если переменная объявлена, но не инициализирован, его значение равняется **не определено**.  
  
 Если переменная не объявлена, его нельзя сравнивать для `undefined`, но вы можете сравнить тип переменной, чтобы строка «undefined».  
  
 `undefined` Константы удобно при явно тестирования или присваивание переменной undefined.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать `undefined` константой.  
  
```JavaScript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## <a name="requirements"></a>Требования  
 `undefined` Свойство появилось в [!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)]и его только для чтения в [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)].  
  
 **Применяется к**: [глобального объекта](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Оператор typeof](../../javascript/reference/typeof-operator-decrementjavascript.md)