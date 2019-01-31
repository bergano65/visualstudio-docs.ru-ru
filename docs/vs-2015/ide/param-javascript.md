---
title: '&lt;PARAM&gt; (JavaScript) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <param> JavaScript XML tag
- param JavaScript XML tag
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a8477de8bf84950d778d4ce843522be35b2d7387
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54772385"
---
# <a name="ltparamgt-javascript"></a>&lt;PARAM&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает сведения о документации для параметра в функции или метода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<param name="parameterName" type="ParameterType"  
    integer="true|false" domElement="true|false"  
    mayBeNull="true|false" elementType="ArrayElementType"  
    elementInteger="true|false" elementDomElement="true|false"  
    elementMayBeNull="true|false" locid="descriptionID"  
    parameterArray="true|false" optional="true|false"  
    value="code">description  
</param>  
```  
  
#### <a name="parameters"></a>Параметры  
 `name`  
 Обязательный. Имя параметра.  
  
 `type`  
 Необязательный параметр. Тип данных параметра. Тип может принимать одно из следующих значений:  
  
- Это язык на ECMAScript введите спецификацией ECMAScript 5, например `Number` и `Object`.  
  
- Объект DOM, таких как `HTMLElement`, `Window`, и `Document`.  
  
- Функция конструктора, JavaScript.  
  
  `integer`  
  Необязательный параметр. Если `type` является `Number`, указывающее, является ли параметр является целым числом. Значение `true` для указания, что параметр является целое число; в противном случае значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
  `domElement`  
  Необязательный параметр. Этот атрибут является устаревшим; `type` атрибут имеет приоритет над этот атрибут. Этот атрибут указывает, является ли параметр документированных DOM-элемента. Значение `true` для указания, что параметр является элементом DOM; в противном случае значение `false`. Если `type` атрибут не задан и `domElement` присваивается `true`, IntelliSense документированных параметр рассматривается как `HTMLElement` при выполнении завершения операторов.  
  
  `mayBeNull`  
  Необязательный параметр. Указывает, можно ли задать параметр документированных в значение null. Значение `true` чтобы указать, что параметр может быть установлено в значение null; в противном случае, значение `false`. Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
  `elementType`  
  Необязательный параметр. Если `type` является `Array`, этот атрибут указывает тип элементов в массиве.  
  
  `elementInteger`  
  Необязательный параметр. Если `type` — `Array` и `elementType` является `Number`, этот атрибут указывает, являются ли элементы в массив целых чисел. Значение `true` для указания, представляют собой целые числа элементов в массиве; в противном случае — значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
  `elementDomElement`  
  Необязательный параметр. Этот атрибут является устаревшим; `elementType` атрибут имеет приоритет над этот атрибут. Если `type` является `Array`, этот атрибут указывает, являются ли элементы в массиве элементов DOM. Значение `true` для указания, элементы являются элементами DOM; в противном случае — значение `false`. Если `elementType` атрибут не задан и `elementDomElement` присваивается `true`, IntelliSense обрабатывает каждый элемент массива в виде `HTMLElement` при выполнении завершения операторов.  
  
  `elementMayBeNull`  
  Необязательный параметр. Если `type` является `Array`, указывает ли элементы в массиве можно задать значение null. Значение `true` чтобы указать, что элементы в массиве может быть установлен в значение null; в противном случае, значение `false`. Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
  `locid`  
  Необязательный параметр. Идентификатор для локализации сведения о параметре. Идентификатор является либо член идентификатор или он соответствует `name` значение в набор сообщений, определяется альянсе метаданных атрибута. Тип идентификатора зависит от формата, указанного в [ \<loc >](../ide/loc-javascript.md) элемент.  
  
  `parameterArray`  
  Необязательный параметр. Указывает ли параметр документированных может повторяться в вызове функции, аналогичную повторяющиеся параметры, поддерживаемые в `String.format` функции. Значение `true` чтобы указать, что параметр может быть повторяющихся; в противном случае, значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.  
  
  `optional`  
  Необязательный параметр. Указывает ли документированных параметр является необязательным в вызывающей функции. Значение `true` чтобы указать, что параметр является необязательным; в противном случае, значение `false`.  
  
  `value`  
  Необязательный параметр. Указывает код, который должен вычисляться для использования с IntelliSense вместо код самой функции. Можно использовать этот атрибут является для предоставления сведений о типе, если тип параметра не определено. Например, можно использовать `value=’1’` обрабатывать тип параметра, как число.  
  
  `description`  
  Необязательный параметр. Описание параметра.  
  
## <a name="remarks"></a>Примечания  
 Является единственным обязательным атрибутом `name`. Все другие атрибуты являются необязательными.  
  
 Элементы, используемые для добавления заметок к функции, такие как [ \<summary >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), и [ \<возвращает >](../ide/returns-javascript.md), необходимо поместить в теле функции до всех операторов.  
  
 При наличии нескольких `<param>` элементы, имеющие одинаковое имя, один из `<param>` элементов используется и избыточные элементы игнорируются. Поведение, которое определяет, какой элемент используется не определен. Если `name` ссылается на несуществующий параметр, то элемент учитывается.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как использовать `<param>` элемент.  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
// Uses of <param> with the value attribute.  
  
function calculate(a) {  
    /// <param name='a' value='1'/>  
    a.    // Completion list for a Number.  
}  
  
function calculate(a) {  
    /// <param name='a' value='{x:0,y:0}'/>  
    a.    // x and y appear in the completion list.  
}  
  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Комментарии XML-документации](../ide/xml-documentation-comments-javascript.md)
