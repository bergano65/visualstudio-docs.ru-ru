---
title: Свойство Multiline (Regular Expression) (JavaScript) | Документы Microsoft
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
- multiline
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- multiline property
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 289cb8d8e103d8c4ac1b1ef06714105d21cba743
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639654"
---
# <a name="multiline-property-regular-expression-javascript"></a>Свойство multiline (Regular Expression) (JavaScript)
Возвращает логическое значение, указывающее состояние флага "multiline" (**m**) используется с регулярным выражением. Значение по умолчанию — **false**. Только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
rgExp.multiline  
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `rgExp` аргумент является экземпляром класса `RegExp` объекта  
  
 **Многострочных** возвращает **true** в случае многострочных флаг установлен для регулярного выражения и возвращает **false** Если это не так. **Многострочных** свойство **true** Если был создан объект регулярного выражения с **m** флаг.  
  
 Если **многострочных** — **false**, «^» соответствует позиции в начале строки, а «$» соответствует позиции в конце строки. Если **многострочных** — **true**, «^» соответствует позиции в начале строки, а также, как положение, следующее «\n» или «\r» и «$» соответствует позиции в конце строки и позиции, предшествующей» \n» "или «\r».  
  
## <a name="example"></a>Пример  
 В следующем примере показано поведение **многострочных** свойство. При передаче «m» в функции, показано ниже, слово «while» заменяется словом «и». Это связано с флагом многострочных задано и слово «while» возникает в начале строки после символа новой строки. Флаг multiline в результаты поиска для выполнения в многострочных строк.  
  
```JavaScript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Применяется к**: [объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Global (Regular Expression)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [Свойство ignoreCase (Regular Expression)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Синтаксис регулярного выражения (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)