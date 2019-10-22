---
title: '&gt; &lt;param (JavaScript) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <param> JavaScript XML tag
- param JavaScript XML tag
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ca6207d22d82e607fa589f944230b36b46e633c2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670357"
---
# <a name="ltparamgt-javascript"></a>&gt; &lt;param (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает сведения о документации для параметра в функции или методе.

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
 `name` Обязательный. Имя параметра.

 `type` Необязательный. Тип данных параметра. Тип может быть одним из следующих:

- Тип языка ECMAScript в спецификации ECMAScript 5, например `Number` и `Object`.

- Объект DOM, например `HTMLElement`, `Window` и `Document`.

- Функция конструктора JavaScript.

  `integer` Необязательный. Если `type` `Number`, указывает, является ли параметр целым числом. Задайте значение `true`, чтобы указать, что параметр является целым числом. в противном случае задайте значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.

  `domElement` Необязательный. Этот атрибут является устаревшим; атрибут `type` имеет приоритет над этим атрибутом. Этот атрибут указывает, является ли задокументированный параметр элементом DOM. Задайте значение `true`, чтобы указать, что параметр является элементом DOM. в противном случае задайте значение `false`. Если атрибут `type` не задан, а `domElement` имеет значение `true`, IntelliSense считает параметр как `HTMLElement` при завершении выполнения инструкции.

  `mayBeNull` Необязательный. Указывает, может ли задокументированный параметр иметь значение null. Задайте значение `true`, чтобы указать, что параметр может иметь значение null. в противном случае задайте значение `false`. Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.

  `elementType` Необязательный. Если `type` является `Array`, этот атрибут указывает тип элементов в массиве.

  `elementInteger` Необязательный. Если `type` — `Array`, а `elementType` — `Number`, этот атрибут указывает, являются ли элементы в массиве целыми числами. Значение `true` указывает, что элементы в массиве являются целыми числами; в противном случае — значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.

  `elementDomElement` Необязательный. Этот атрибут является устаревшим; атрибут `elementType` имеет приоритет над этим атрибутом. Если `type` — `Array`, этот атрибут указывает, являются ли элементы в массиве элементами DOM. Значение `true` указывает, что элементы являются элементами DOM; в противном случае используется значение `false`. Если атрибут `elementType` не задан, а для `elementDomElement` установлено `true`, IntelliSense считает каждый элемент в массиве как `HTMLElement` при выполнении завершения операторов.

  `elementMayBeNull` Необязательный. Если `type` является `Array`, указывает, могут ли элементы в массиве принимать значение NULL. Значение `true` указывает, что элементы в массиве могут принимать значение NULL; в противном случае — значение `false`. Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.

  `locid` Необязательный. Идентификатор для сведений о локализации параметра. Идентификатор является идентификатором члена или соответствует значению атрибута `name` в наборе сообщений, определенном метаданными OpenAjax. Тип идентификатора зависит от формата, указанного в элементе [\<loc>](../ide/loc-javascript.md).

  `parameterArray` Необязательный. Указывает, может ли задокументированный параметр повторяться в вызове функции, аналогично повторяющимся параметрам, поддерживаемым в функции `String.format`. Задайте значение `true`, чтобы указать, что параметр может повторяться; в противном случае задайте значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.

  `optional` Необязательный. Указывает, является ли задокументированный параметр необязательным в вызывающей функции. Задайте значение `true`, чтобы указать, что параметр является необязательным. в противном случае задайте значение `false`.

  `value` Необязательный. Указывает код, который должен быть вычислен для использования IntelliSense вместо самого кода функции. Этот атрибут можно использовать для предоставления сведений о типе, если тип параметра не определен. Например, можно использовать `value=’1’`, чтобы считать тип параметра числом.

  `description` Необязательный. Описание параметра.

## <a name="remarks"></a>Примечания
 Единственным обязательным атрибутом является `name`. Все остальные атрибуты являются необязательными.

 Элементы, используемые для комментирования функций, таких как [\<summary >](../ide/summary-javascript.md), [\<param >](../ide/param-javascript.md)и [\<returns](../ide/returns-javascript.md)>, должны быть помещены в тело функции перед любыми инструкциями.

 Если имеется несколько `<param>` элементов с одинаковым именем, используется один из элементов `<param>`, а избыточные элементы игнорируются. Поведение, определяющее, какой элемент используется, не определен. Если `name` ссылается на несуществующий параметр, элемент игнорируется.

## <a name="example"></a>Пример
 В следующем примере кода показано использование элемента `<param>`.

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

## <a name="see-also"></a>См. также
 [Комментарии XML-документации](../ide/xml-documentation-comments-javascript.md)
