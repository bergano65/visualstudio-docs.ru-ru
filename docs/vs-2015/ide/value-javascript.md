---
title: '&lt;значение &gt; (JavaScript) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aefe710cc730d5624abc01bbdfc54d9961788787
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656399"
---
# <a name="ltvaluegt-javascript"></a>&lt;значение &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает сведения о документации `get` для `set` функций и для свойств ECMAScript 3.

## <a name="syntax"></a>Синтаксис

```
<value type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID">description
</value>
```

#### <a name="parameters"></a>Параметры
 `type` Необязательный. Тип данных свойства. Тип может быть одним из следующих:

- Тип языка ECMAScript в спецификации ECMAScript 5, например `Number` и `Object`.

- Объект DOM, например `HTMLElement`, `Window` и `Document`.

- Функция конструктора JavaScript.

  `integer` Необязательный. Если `type` имеет значение `Number` , указывает, является ли свойство целым числом. Задайте значение, чтобы `true` указать, что свойство является целым числом; в противном случае задайте для значение `false` . Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.

  `domElement` Необязательный. Этот атрибут является устаревшим; атрибут `type` имеет приоритет над этим атрибутом. Этот атрибут указывает, является ли задокументированное свойство элементом DOM. Задайте значение, чтобы `true` указать, что свойство является ЭЛЕМЕНТОМ DOM; в противном случае задайте для значение `false` . Если `type` атрибут не задан и `domElement` имеет значение `true` , IntelliSense рассматривает задокументированное свойство как `HTMLElement` при завершении выполнения инструкции.

  `mayBeNull` Необязательный. Указывает, может ли задокументированное свойство иметь значение null. Задайте значение, чтобы `true` указать, что свойство может иметь значение null. в противном случае задайте значение `false` . Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.

  `elementType` Необязательный. Если `type` является `Array`, этот атрибут указывает тип элементов в массиве.

  `elementInteger` Необязательный. Если `type` — `Array`, а `elementType` — `Number`, этот атрибут указывает, являются ли элементы в массиве целыми числами. Значение `true` указывает, что элементы в массиве являются целыми числами; в противном случае — значение `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.

  `elementDomElement` Необязательный. Этот атрибут является устаревшим; атрибут `elementType` имеет приоритет над этим атрибутом. Если `type` — `Array`, этот атрибут указывает, являются ли элементы в массиве элементами DOM. Значение `true` указывает, что элементы являются элементами DOM; в противном случае используется значение `false`. Если атрибут `elementType` не задан, а для `elementDomElement` установлено `true`, IntelliSense считает каждый элемент в массиве как `HTMLElement` при выполнении завершения операторов.

  `elementMayBeNull` Необязательный. Если `type` является `Array`, указывает, могут ли элементы в массиве принимать значение NULL. Значение `true` указывает, что элементы в массиве могут принимать значение NULL; в противном случае — значение `false`. Значение по умолчанию — `false`. Этот атрибут не используется средой Visual Studio для предоставления сведений IntelliSense.

  `locid` Необязательный. Идентификатор для сведений о локализации свойства. Идентификатор является идентификатором члена или соответствует значению атрибута `name` в наборе сообщений, определенном метаданными OpenAjax. Тип идентификатора зависит от формата, указанного в [\<loc>](../ide/loc-javascript.md) элементе.

  `description` Необязательный. Описание свойства.

## <a name="remarks"></a>Remarks
 Свойства ECMAScript 5 используют [\<summary>](../ide/summary-javascript.md) элемент.

 Используйте `<value>` элемент непосредственно перед `get` `set` функцией или.

## <a name="example"></a>Пример
 В следующем примере кода показано, как использовать `<value>` элемент `get` функции.

```javascript
function Sys$CancelEventArgs$get_cancel() {
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>
    if (arguments.length !== 0) throw Error.parameterCount();
    return this._cancel();
}
```

## <a name="see-also"></a>См. также:
 [Комментарии XML-документации](../ide/xml-documentation-comments-javascript.md)
