---
title: Свойство ignoreCase (Regular Expression) (JavaScript) | Документы Microsoft
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
- ignoreCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- IgnoreCase property
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ae9fee8e6303fb944f59c11c173f9e8b7f7cc75a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637864"
---
# <a name="ignorecase-property-regular-expression-javascript"></a>Свойство ignoreCase (Regular Expression) (JavaScript)
Возвращает логическое значение, указывающее состояние флага ignoreCase (**я**) используется с регулярным выражением. Значение по умолчанию — **false**. Только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
rgExp.ignoreCase  
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `rgExp` ссылка представляет собой экземпляр `RegExp` объекта.  
  
 **IgnoreCase** возвращает **true** Если флаг ignoreCase установлен для регулярного выражения и возвращает **false** Если это не так.  
  
 Флаг ignoreCase при использовании указывает, что следует учитывать регистр при сопоставлении шаблона в строке.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **ignoreCase** свойство. При передаче «gi» в показанную ниже функцию, все экземпляры слова «» будут заменены слова «», включая начальные «». Это связано с установленным флагом ignoreCase, процедура поиска пропускает без учета регистра. Поэтому «T» совпадает со значением «t» в целях соответствия.  
  
 Эта функция возвращает логические значения, которые указывают состояние допустимых флагов регулярных выражений, которые являются **g**, **я**, и **m**. Функция также возвращает строку, которую были внесены все.  
  
```JavaScript  
function RegExpPropDemo(flag){  
    // The flag parameter is a string that contains  
    // g, i, or m. The flags can be combined.  
  
    // Check flags for validity.  
    if (flag.match(/[^gim]/))  
        {  
        return ("Flag specified is not valid");  
        }  
  
    // Create the string on which to perform the replacement.  
    var orig = "The batter hit the ball with the bat ";  
    orig += "and the fielder caught the ball with the glove.";  
  
    // Replace "the" with "a".  
    var re = new RegExp("the", flag);  
    var r = orig.replace(re, "a");          
  
    // Output the resulting string and the values of the flags.  
    var s = "";  
    s += "global: " + re.global.toString();  
    s += "<br />";  
    s += "ignoreCase: " + re.ignoreCase.toString();  
    s += "<br />";  
    s += "multiline: " + re.multiline.toString();  
    s += "<br />";  
    s += "Resulting String: " + r;  
    s += "<br />";  
    s += "<br />";  
    return (s);  
}  
  
document.write(RegExpPropDemo("gi"));  
document.write(RegExpPropDemo("g"));  
```  
  
## <a name="example"></a>Пример  
 Ниже приведен результат.  
  
```JavaScript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Применяется к**: [объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство Global (Regular Expression)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [Свойство Multiline (Regular Expression)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Синтаксис регулярного выражения (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)