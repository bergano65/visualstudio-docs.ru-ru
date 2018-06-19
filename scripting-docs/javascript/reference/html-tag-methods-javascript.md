---
title: Методы HTML-тегов (JavaScript) | Документы Microsoft
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
helpviewer_keywords:
- link method [JavaScript]
- blink method [JavaScript]
- fontsize method [JavaScript]
- italics method [JavaScript]
- sup method [JavaScript]
- anchor method [JavaScript]
- fixed method [JavaScript]
- fontcolor method [JavaScript]
- bold method [JavaScript]
- small method [JavaScript]
- HTML Tag methods [JavaScript]
- sub method [JavaScript]
- big method [JavaScript]
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7639bc609d8e9b7e4b212fe67ae40f81487d708e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638654"
---
# <a name="html-tag-methods-javascript"></a>Методы HTML-тегов (JavaScript)
Методы HTML-тег используется для размещения элементов HTML вокруг текста в `String` объекта.  
  
## <a name="syntax"></a>Синтаксис  
 В следующей таблице перечислены синтаксис и описание каждого метода тег HTML.  
  
 В столбце синтаксис `string1` — `String` объект или литерал.  
  
 Указывает стандартный столбец [World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/?LinkId=199553) рекомендации для HTML 4. «Рекомендуется» указывает, HTML-элемента не рекомендуется использовать таблицы стилей.  
  
|Синтаксис|Описание метода|Описание параметра|Стандартный|  
|------------|------------------------|---------------------------|--------------|  
|`string1`.Anchor (`name`)|Помещает привязку HTML, имеющий атрибут NAME вокруг текста.|`name` Параметр является для перевода в атрибуте NAME HTML-привязкой.||  
|`string1`.Big()|Помещает HTML \<BIG > теги вокруг текста.||Рекомендуется не использовать|  
|`string1`.BLINK()|Помещает HTML \<BLINK > теги вокруг текста. \<BLINK > тег не поддерживается в обозревателе Internet Explorer.||Не в стандартном|  
|`string1`.bold()|Помещает HTML \<B > теги вокруг текста.||Рекомендуется не использовать|  
|`string1`.fixed()|Помещает HTML \<TT > теги вокруг текста.||Рекомендуется не использовать|  
|`string1`.FontColor (`color`)|Помещает HTML \<ШРИФТА > тегов с атрибутом COLOR вокруг текста.|`color` Является значением строку, содержащую шестнадцатеричное значение цвета или предварительно определенное имя цвета. Допустимые стандартные имена цветов зависят от [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] размещения браузера и его версия.|Рекомендуется использовать|  
|`string1`.FontSize (`size`)|Помещает HTML \<ШРИФТА > тегов с атрибутом SIZE вокруг текста.|`size` Параметра является целое число, указывающее размер текста. Действительные целочисленные значения зависят от [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] размещения браузера и его версия.|Рекомендуется использовать|  
|`string1`.italics()|Помещает HTML \<я > теги вокруг текста.||Рекомендуется не использовать|  
|`string1`.Link (`href`)|Помещает привязку HTML, имеющего атрибут HREF вокруг текста.|`href` Параметр является для перевода в атрибуте HREF HTML-привязкой.||  
|`string1`.Small()|Помещает HTML \<SMALL > теги вокруг текста.||Рекомендуется не использовать|  
|`string1`.Strike()|Помещает HTML \<STRIKE > теги вокруг текста.||Рекомендуется использовать|  
|`string1`.Sub()|Помещает HTML \<SUB > теги вокруг текста.|||  
|`string1`.SUP()|Помещает HTML \<SUP > теги вокруг текста.|||  
  
## <a name="remarks"></a>Примечания  
 Проверка не выполняется, чтобы определить, является ли HTML-теги, уже были применены к строке.  
  
## <a name="example"></a>Пример  
 Следующие примеры показывают, как использовать методы тегов HTML.  
  
```JavaScript  
// anchor method.  
var strVariable = "This is an anchor.";  
document.write(strVariable.anchor("Anchor1"));  
// Output: <A NAME="Anchor1">This is an anchor.</A>  
  
// big method.  
var strVariable = "This is a string.";  
document.write(strVariable.big());  
// Output: <BIG>This is a string.</BIG>  
  
//  blink method.  
var strVariable = "This is a string.";  
document.write(strVariable.blink());  
// Output: <BLINK>This is a string.</BLINK>  
  
//  bold method.  
var strVariable = "This is a string.";  
document.write(strVariable.bold());  
// Output: <B>This is a string.</B>  
  
//  fixed method.  
var strVariable = "This is a string.";  
document.write(strVariable.fixed());  
// Output: <TT>This is a string.</TT>  
  
//  fontcolor method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontcolor("red"));  
// Output: <FONT COLOR="red">This is a string.</FONT>  
  
//  fontsize method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontsize(-1));  
// Output: <FONT SIZE="-1">This is a string.</FONT>  
  
//  italics method  
var strVariable = "This is a string.";  
document.write(strVariable.italics());  
// Output: <I>This is a string.</I>  
  
//  link method.  
var strVariable = "This is a hyperlink.";  
document.write(strVariable.link("http://www.microsoft.com"));  
// Output: <A HREF="http://www.microsoft.com">This is a hyperlink.</A>  
  
//  small method.  
var strVariable = "This is a string.";  
document.write(strVariable.small());  
// Output: <SMALL>This is a string.</SMALL>  
  
//  strike method.  
var strVariable = "This is a string.";  
document.write(strVariable.strike());  
// Output: <STRIKE>This is a string.</STRIKE>  
  
//  sub method.  
var strVariable = "This is a string.";  
document.write(strVariable.sub());  
// Output: <SUB>This is a string.</SUB>  
  
//  sup method.  
var strVariable = "This is a string.";  
document.write(strVariable.sup());  
// Output: <SUP>This is a string.</SUP>  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применяется к**: [строковый объект](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Объект String](../../javascript/reference/string-object-javascript.md)