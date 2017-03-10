---
title: "JavaScript IntelliSense | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 63
author: mikejo
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: d07820eda0d76163d99d7752789750eaf56182fd
ms.openlocfilehash: 1f8372fe201d6b23ee2c65e0f6d6a2fa28976654
ms.lasthandoff: 02/22/2017

---
# <a name="javascript-intellisense"></a>IntelliSense для JavaScript
[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] обеспечивает эффективное редактирование JavaScript. Система Visual Studio, основанная на языковой службе TypeScript, расширяет возможности IntelliSense, поддерживает современные компоненты JavaScript, а также улучшенные функции для повышения эффективности работы, такие как "Перейти к определению", рефакторинг и многое другое.

> [!NOTE]
>  Языковая служба JavaScript в [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] использует новый механизм языковой службы ("сальса"). Дополнительные сведения можно получить в этом разделе, а также в этой [записи блога](https://blogs.msdn.microsoft.com/visualstudio/2016/04/08/previewing-salsa-javascript-language-service-visual-studio-15/). Новые возможности редактирования в основном относятся к VS Code. Дополнительные сведения см. в [документах о VS Code](https://code.visualstudio.com/docs/languages/javascript).

Дополнительные сведения об общих функциональных возможностях IntelliSense в [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] см. в разделе [Использование технологии IntelliSense](../ide/using-intellisense.md). 

## <a name="whats-new-in-the-javascript-language-service-in-includevsdev15miscincludesvsdev15mdmd"></a>Новые возможности языковой службы JavaScript в [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

- Расширение функций IntelliSense

    JavaScript IntelliSense в [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] теперь отображает гораздо больше информации в списках элементов и параметров.
Эта новая информация предоставляется языковой службой TypeScript, которая использует статический анализ, чтобы помочь вам лучше понять код.
Для формирования такой информации TypeScript использует несколько источников.
    - [IntelliSense на основе определения типа](#TypeInference)
    - [IntelliSense на основе JSDoc](#JsDoc)
    - [IntelliSense на основе файлов объявления TypeScript](#TSDeclFiles)

- [Автоматическое получение определений типов](#Auto)
- [Поддержка ES6 и более поздних версий](#ES6)
- [Поддержка синтаксиса JSX](#JSX)

## <a name="TypeInference"></a>IntelliSense на основе определения типа
В большинстве случаев явные сведения о типах в JavaScript недоступны. Однако тип обычно довольно легко вывести из контекста кода.
Этот процесс называется определением типа.

Для переменной или свойства типом обычно является тип значения, используемый для его инициализации, либо последнее присвоенное значение. 

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Для функции тип возвращаемого значения можно вывести из операторов return. 

Для параметров функций вывод сейчас отсутствует, однако это можно обойти с помощью файлов `.d.ts` TypeScript или JSDoc (см. в следующих разделах).

Кроме того, есть специальный вывод для следующих элементов:
 - Классы в стиле ES3, определяемые с использованием функции конструктора и назначений свойству прототипа.
 - Шаблоны модуля в стиле CommonJS, указанные в качестве назначений свойств для объекта `exports` или назначений свойству `module.exports`.

```js
function Foo(param1) {
    this.prop = param1;
}
Foo.prototype.getIt = function () { return this.prop; };
// Foo will appear as a class, and instances will have a 'prop' property and a 'getIt' method.

exports.Foo = Foo;
// This file will appear as an external module with a 'Foo' export.
// Note that assigning a value to "module.exports" is also supported.
```

## <a name="JsDoc"></a> IntelliSense на основе JSDoc

Когда определение типа не предоставляет нужные сведения о типе (или требуется вести документацию), их можно предоставить явно с помощью заметок JSDoc.  Например, чтобы назначить определенный тип частично объявленному объекту, можно использовать тег `@type`, как показано ниже:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Как уже упоминалось, параметры функции никогда не выводятся. Однако с помощью тега `@param` JSDoc можно добавить типы и в параметры функции. 

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```
 
Сведения о поддерживаемых сейчас заметках JsDoc см. в [этом документе](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript).

## <a name="TsDeclFiles"></a> IntelliSense на основе файлов объявления TypeScript

Так как JavaScript и TypeScript теперь основаны одной языковой службе, они способны полнее взаимодействовать друг с другом. Например, JavaScript IntelliSense можно предоставить для значений, объявленных в файле `.d.ts` ([подробнее](https://github.com/Microsoft/TypeScript-Handbook/blob/master/pages/Writing%20Definition%20Files.md)), а типы, такие как интерфейсы и классы, объявленные в TypeScript, доступны для использования в качестве типов в комментариях JsDoc. 

Ниже показан простой пример файла определения TypeScript, предоставляющий подобные сведения о типе (через интерфейс) файлу JavaScript в том же проекте (с помощью тега JsDoc).

_**Объявления TypeScript, используемые в JavaScript**_

<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png" height="400" width="640"/>

## <a name="Auto"></a> Автоматическое получение определений типов
В среде TypeScript API наиболее популярных библиотек JavaScript описываются файлами `.d.ts`, а наиболее распространенным репозиторием для таких определений является [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

По умолчанию языковая служба языка сальса будет пытаться определить используемые библиотеки JavaScript, а затем автоматически скачать и указать в ссылке соответствующий файл `.d.ts`, описывающий эту библиотеку, чтобы расширить возможности IntelliSense. Файлы скачиваются в кэш, расположенный в пользовательской папке в `%LOCALAPPDATA%\Microsoft\TypeScript`. 

> [!NOTE]
> Эта функция **отключена** по умолчанию при использовании файла конфигурации `tsconfig.json`, но ее можно включить, воспользовавшись описанием ниже.

Сейчас автоматическое определение работает для зависимостей, скачанных из npm (путем чтения файла `package.json`), Bower (путем чтения файла `bower.json`) и свободных файлов в проекте, которые примерно соответствуют списку из 400 наиболее популярных библиотек JavaScript. Например, если у вас в проекте есть `jquery-1.10.min.js`, для расширения возможностей редактирования будет получен и загружен файл `jquery.d.ts`. Этот файл `.d.ts` не оказывает влияния на проект. 

Если вы не хотите использовать автоматическое получение, отключите его, добавив указанный ниже файл конфигурации. Вы по-прежнему можете вручную поместить файлы определений для использования непосредственно в проекте.

## <a name="ES6"></a> Поддержка ES6 и более поздних версий

ES6 или ECMAScript 2015 — это следующая версия JavaScript. В ней появился новый синтаксис языка, например классы, стрелочные функции, `let`/`const` и многое другое. Весь этот новый синтаксис поддерживается в Visual Studio.

Одной из ключевых функций, предоставляемых TypeScript, является возможность использования функций ES6 и создания кода, который может выполняться в средах выполнения JavaScript, пока не поддерживающих эти новые функции. Часто это называется "транспилированием". Так как среда JavaScript использует ту же языковую службу, она тоже может использовать преимущества транспилирования ES6+ в ES5.

Перед соответствующей настройкой нужно разобраться в доступных параметрах конфигурации.  TypeScript настраивается с помощью файла `tsconfig.json`. При отсутствии такого файла используются значения по умолчанию. Для обеспечения совместимости эти значения по умолчанию отличаются, если присутствуют только файлы JavaScript (и, возможно, файлы `.d.ts`). Для компиляции файлов JavaScript нужно добавить файл `tsconfig.json`, а затем явным образом задать некоторые из этих значений по умолчанию.

Ниже описаны обязательные параметры для файла tsconfig:

 - `allowJs`: это значение должно быть равно `true` для распознавания файлов JavaScript.
По умолчанию оно равно `false`, так как TypeScript компилируется в JavaScript, кроме того, это не позволяет компилятору включать только что скомпилированные файлы.
 - `outDir`: в этом параметре нужно задать расположение, не включенное в проект, чтобы выдаваемые файлы JavaScript не обнаруживались и не включались в проект (см. `exclude` ниже).
 - `module`: при использовании модулей этот параметр указывает компилятору, какой формат модулей должен использовать создаваемый код (например, `commonjs` для узла или средств увязки в пакеты, таких как Browserify).
 - `exclude`: этот параметр указывает папки, которые не нужно включать в проект. 
 В него следует добавить выходное расположение, а также не относящиеся к проекту папки, такие как `node_modules` или `temp`.
 - `enableAutoDiscovery`: этот параметр включает автоматическое обнаружение и скачивание файлов определений, как описано выше.
 - `compileOnSave`: этот параметр указывает компилятору, следует ли повторять компиляцию при каждом сохранении файла исходного кода в Visual Studio.

Чтобы преобразовать файлы JavaScript в модули CommonJS в папке `./out`, в файл `tsconfig.json` можно включить параметры, аналогичные приведенным ниже.

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "allowJs": true,
    "outDir": "out"
  },
  "exclude": [
    "node_modules",
    "wwwroot",
    "out"
  ],
  "compileOnSave": true,
  "typingOptions": {
    "enableAutoDiscovery": true
  }
}
```

При задании указанных выше параметры существующий исходный файл (`./app.js`) одержит несколько функций языка ECMAScript 2015, как показано ниже:

```js
import {Subscription} from 'rxjs/Subscription';

class Foo {
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;
    }
}

export let sqr = x => x * x;
export default Subscription;
```

Затем файл будет выдан в `./out/app.js`, нацеленный на ECMAScript 5 (по умолчанию), что выглядит примерно следующим образом:

```js
"use strict";
var Subscription_1 = require('rxjs/Subscription');
var Foo = (function () {
    function Foo() {
    }
    Foo.prototype.sayHi = function (name) {
        return "Hi " + name + ", welcome to Salsa!";
    };
    return Foo;
}());
exports.sqr = function (x) { return x * x; };
Object.defineProperty(exports, "__esModule", { value: true });
exports.default = Subscription_1.Subscription;
//# sourceMappingURL=app.js.map
```

## <a name="JSX"></a> Поддержка синтаксиса JSX

JavaScript в Visual Studio 2017 обладает обширной поддержкой синтаксиса JSX. JSX — это набор синтаксиса, позволяющий использовать HTML-теги в файлах JavaScript. 

На приведенном ниже рисунке показан определенный в файле `comps.tsx` TypeScript компонент React, который затем используется из файла `app.jsx` с применением IntelliSense для завершений и документации в выражениях JSX.
TypeScript здесь не требуется, просто этот конкретный пример содержит некоторый объем кода TypeScript.
<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/react.png" height="500" width="640"/>

> [!NOTE]
> Для преобразования синтаксиса JSX вызовы React нужно добавить параметр `"jsx": "react"` в `compilerOptions` в указанном выше файле `tsconfig.json`.

Файл JavaScript, созданный в "./out/app.js" при сборке, будет содержать этот код:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

