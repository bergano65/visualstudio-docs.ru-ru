---
title: '&gt; &lt;field (JavaScript) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a3fc786e4d99d1eaff4a8b152ea9496ce8400ff1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663860"
---
# <a name="ltfieldgt-javascript"></a>&gt; &lt;field (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает сведения о документации, включая описание, для поля или элемента, определенного для объекта.

## <a name="syntax"></a>Синтаксис

```
<field name="fieldName" static="true|false"
    type="FieldType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    helpKeyword="keyword" locid="descriptionID"
    value="code">description
</field>
```

#### <a name="parameters"></a>Параметры
 `name` имя поля или элемента. Если элемент `<field>` используется в функции-конструкторе, `name` является обязательным и определяет элемент, к которому применяется тег. Если элемент `<field>` непосредственно замещает поле, этот атрибут игнорируется, а имя, используемое Visual Studio, является именем фактического поля в исходном коде.

 `static` Необязательный. Указывает, является ли поле членом функции конструктора или членом объекта, возвращаемого функцией конструктора. Задайте значение `true`, чтобы считать поле членом функции конструктора. Задайте значение `false`, чтобы считать поле членом объекта, возвращаемого функцией конструктора.

 `type` Необязательный. Тип данных поля. Тип может быть одним из следующих:

- Тип языка ECMAScript в спецификации ECMAScript 5, например `Number` и `Object`.

- Объект DOM, например `HTMLElement`, `Window` и `Document`.

- Функция конструктора JavaScript.

  `integer` Необязательный. Если `type` `Number`, указывает, является ли поле целым числом. Задайте значение `true`, чтобы указать, что поле является целым числом. в противном случае задайте значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.

  `domElement` Необязательный. Этот атрибут является устаревшим; атрибут `type` имеет приоритет над этим атрибутом. Этот атрибут указывает, является ли задокументированное поле элементом DOM. Задайте значение `true`, чтобы указать, что поле является элементом DOM; в противном случае задайте значение `false`. Если атрибут `type` не задан и `domElement` имеет значение `true`, IntelliSense рассматривает заданное поле как `HTMLElement` при завершении выполнения инструкции.

  `mayBeNull` Необязательный. Указывает, может ли задокументированное поле иметь значение null. Задайте значение `true`, чтобы указать, что поле может иметь значение null. в противном случае задайте значение `false`. Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.

  `elementType` Необязательный. Если `type` является `Array`, этот атрибут указывает тип элементов в массиве.

  `elementInteger` Необязательный. Если `type` — `Array`, а `elementType` — `Number`, этот атрибут указывает, являются ли элементы в массиве целыми числами. Значение `true` указывает, что элементы в массиве являются целыми числами; в противном случае — значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.

  `elementDomElement` Необязательный. Этот атрибут является устаревшим; атрибут `elementType` имеет приоритет над этим атрибутом. Если `type` — `Array`, этот атрибут указывает, являются ли элементы в массиве элементами DOM. Значение `true` указывает, что элементы являются элементами DOM; в противном случае используется значение `false`. Если атрибут `elementType` не задан, а для `elementDomElement` установлено `true`, IntelliSense считает каждый элемент в массиве как `HTMLElement` при выполнении завершения операторов.

  `elementMayBeNull` Необязательный. Если `type` является `Array`, указывает, могут ли элементы в массиве принимать значение NULL. Значение `true` указывает, что элементы в массиве могут принимать значение NULL; в противном случае — значение `false`. Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.

  `helpKeyword` Необязательный. Ключевое слово для справки F1.

  `locid` Необязательный. Идентификатор для сведений о локализации поля. Идентификатор является идентификатором члена или соответствует значению атрибута `name` в наборе сообщений, определенном метаданными OpenAjax. Тип идентификатора зависит от формата, указанного в теге [\<loc>](../ide/loc-javascript.md).

  `value` Необязательный. Указывает код, который должен быть вычислен для использования IntelliSense вместо самого кода функции. Для `<field>` этот атрибут поддерживается для функций-конструкторов, но не поддерживается для объектных литералов. Этот атрибут можно использовать для предоставления сведений о типе, если тип поля не определен. Например, можно использовать `value=’1’`, чтобы считать тип поля числом.

  `description` Необязательный. Описание поля.

## <a name="remarks"></a>Примечания
 Атрибут `name` является обязательным при документировании поля в функции конструктора. Для всех других сценариев все атрибуты элемента `<field>` являются необязательными.

 При документировании функции-конструктора элемент `<field>` должен появляться непосредственно перед объявлением поля. Атрибут `name` должен совпадать с именем поля, которое используется в исходном коде. Для членов объекта атрибут `name` можно опустить, если элемент `<field>` появляется непосредственно перед объявлением члена объекта.

## <a name="example"></a>Пример
 В следующем примере кода показано использование элемента `<field>`.

```javascript
// Use of <field> in an object definition.
var Rectangle = {
    /// <field type='Number'>The width of the rectangle.</field>
    wid: 5,
    /// <field type='Number'>The length of the rectangle.</field>
    len: 0,
    /// <field type='Number'>Returns the area of the rectangle.</field>
    getArea: function (wid, len) {
        return len * wid;
    }
}

// Use of <field> in a constructor function.
// The name attribute is required.
function Engine() {
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
    this.HorsePower = 150;
}
```

## <a name="example"></a>Пример
 В следующем примере показано, как использовать элемент `<field>` с атрибутом `static`, для которого задано значение `true`.

```javascript
function Engine() {
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>
}

Engine.HorsePower = 140;
// IntelliSense on the field is available here.
Engine.

```

## <a name="example"></a>Пример
 В следующем примере показано, как использовать элемент `<field>` с атрибутом `static`, для которого задано значение `false`.

```javascript
function Engine() {
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>
}

Engine.HorsePower = 140;
var eng = new Engine();
// IntelliSense on the field is available here.
eng.

```

## <a name="example"></a>Пример
 В следующем примере показано, как использовать элемент `<field>` с атрибутом `value`.

```javascript
function calculator(a) {
    /// <field name='f' value='1'/>
}
new calculator().f.   // Completion list for a Number.

```

## <a name="see-also"></a>См. также
 [Комментарии XML-документации](../ide/xml-documentation-comments-javascript.md)
