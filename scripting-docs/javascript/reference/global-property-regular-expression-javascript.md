---
title: Свойство Global (Regular Expression) (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Global
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- global property
ms.assetid: 76a0f115-0d89-4aca-86d5-932895c6d649
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e2b0256fea60b7ab998c504e79565fc7028cd98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637434"
---
# <a name="global-property-regular-expression-javascript"></a>Свойство global (Regular Expression) (JavaScript)
Возвращает логическое значение, указывающее состояние глобального флага (**g**) используется с регулярным выражением. Значение по умолчанию — **false**. Только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
rgExp.global  
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `rgExp` ссылка представляет собой экземпляр **регулярное выражение** объекта.  
  
 `global` Возвращает **true** Если глобальный флаг установлен для регулярного выражения и возвращает **false** Если это не так.  
  
 Глобальный флаг, при использовании указывает, что следует найти все вхождения шаблона в строке, не только первый из них. Это также называется глобальным соответствием.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование `global` свойство. Если передать **g** в функции, показано ниже, все экземпляры слова «» будут заменены слова «». Обратите внимание, что «» в начале строки не заменяется поскольку **я** (не учитывать регистр) флаг не передается в функцию.  
  
 Эта функция отображает условие свойства, связанные с допустимых флагов регулярных выражений, которые являются **g**, **я**, и **m**. Функция также отображает строку, которую были внесены все.  
  
```JavaScript  
function RegExpPropDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The batter hit the ball with the bat ";  
   ss += "and the fielder caught the ball with the glove.";  
  
   //Replace "the" with "a".  
   var re = new RegExp("the", flag);  
   var r = ss.replace(re, "a");          
  
   // Output the resulting string and the flags.  
   var s = "";  
   s += "global: " + re.global.toString();  
   s += "<br />";  
   s += "ignoreCase: " + re.ignoreCase.toString();  
   s += "<br />";  
   s += "multiline: " + re.multiline.toString();  
   s += "<br />";  
   s += "Resulting String: " + r;  
  
   return (s);  
}  
  
document.write(RegExpPropDemo("g"));  
```  
  
## <a name="example"></a>Пример  
 Ниже приведен результат.  
  
```JavaScript  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Применяется к**: [объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство ignoreCase (Regular Expression)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Свойство Multiline (Regular Expression)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Синтаксис регулярного выражения (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)