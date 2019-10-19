---
title: Создание комментариев JSDoc для JavaScript IntelliSense | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b974f3450b88ab22e58e284881f270c1b3d72298
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619277"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>Создание комментариев JSDoc для JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Технология IntelliSense в Visual Studio отображает сведения, которые добавляются в скрипт с помощью стандартных комментариев JSDoc. Комментарии JSDoc можно использовать для предоставления сведений об элементах кода, например о функциях, полях и переменных.

## <a name="jsdoc-comment-tags"></a>Теги для комментариев JSDoc
 В технологии IntelliSense для отображения сведений о коде используются следующие стандартные теги для комментариев JSDoc.

|  Тег JSDoc   |                       Синтаксис                        |                                                     Примечания                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              @deprecated *описание*              |                                   Указывает устаревшую функцию или метод.                                   |
| @description |             @description *описание*              |                              Указывает описание для функции или метода.                               |
|    @param    | @param {*Type*}<em>Описание</em> ParameterName | Указывает сведения для параметра в функции или методе.<br /><br /> TypeScript также поддерживает @paramTag. |
|  @property   |          @property {*тип*} *имя_свойства*          |   Указывает сведения, включая описание, для поля или элемента, который определен в объекте.    |
|   @returns   |                  @returns {*тип*}                  |           Указывает возвращаемое значение.<br /><br /> Для TypeScript используйте @returnType вместо @returns.           |
|   @summary   |               @summary *описание*                |                   Задает описание функции или метода (то же, что @description).                   |
|    @type     |                   @type {*тип*}                    |                                Указывает тип для константы или переменной.                                |
|   @typedef   |         @typedef {*тип*} *пользовательское_имя_свойства*          |                                            Указывает пользовательский тип.                                            |

### <a name="examples"></a>Примеры
 В следующем примере показано использование тегов @description, @param и @return JSDoc для функции с именем `getArea`.

```javascript
/** @description Determines the area of a circle that has the specified radius parameter.
 * @param {number} radius The radius of the circle.
 * @return {number}
 */
function getArea(radius) {
    var areaVal;
    areaVal = Math.PI * radius * radius;
    return areaVal;
}
```

 В предыдущем примере IntelliSense отображает описание, параметры и возвращаемые сведения при вводе открывающей скобки для `getArea`.

 ![Сведения об IntelliSense для функции](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")

 В следующем примере показано, как использовать тег @typedef с тегом @property.

```javascript
/**
  * @typedef {object} Weather
  * @property {string} current The current weather.
  */
function getForecast(Weather) {
}

var w = new Weather();
```

 В следующем примере показано использование тегов @type JSDoc. Как показано в этом примере, одиночные звездочки (*), которые следуют за начальными двойными звездочками (\*\*), не являются обязательными.

```javascript
/**
    @type {string}
*/
const RED = 'FF0000';

```

 В следующем примере показано, как использовать тег @deprecated JSDoc.

```javascript
/**
 * @deprecated since version 2.0
 */
function old() {
}
```
