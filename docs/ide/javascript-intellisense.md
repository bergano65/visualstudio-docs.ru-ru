---
title: IntelliSense для JavaScript
description: Узнайте, как Visual Studio предоставляет широкие возможности IntelliSense, обеспечивает поддержку современных функций JavaScript и улучшенных функций для повышения производительности.
ms.custom: SEO-VS-2020
ms.date: 06/28/2017
ms.topic: conceptual
ms.technology: vs-javascript
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5a4120a6038949f172b96bec599f2329b69abcac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903968"
---
# <a name="javascript-intellisense"></a>IntelliSense для JavaScript

Visual Studio обеспечивает эффективное редактирование JavaScript без дополнительной подготовки. Система Visual Studio, основанная на языковой службе TypeScript, расширяет возможности IntelliSense, поддерживает современные компоненты JavaScript, а также улучшенные функции для повышения эффективности работы, такие как "Перейти к определению", рефакторинг и многое другое.

> [!NOTE]
> Начиная с Visual Studio 2017 языковая служба JavaScript использует новый механизм языковой службы ("сальса"). Дополнительные сведения можно получить в этой статье, а также в этой [записи блога](https://devblogs.microsoft.com/visualstudio/previewing-salsa-javascript-language-service-visual-studio-15/). Новые возможности редактирования в основном относятся к Visual Studio Code. Дополнительные сведения см. в [документах о VS Code](https://code.visualstudio.com/docs/languages/javascript).

Дополнительные сведения об общих функциональных возможностях IntelliSense в Visual Studio см. в разделе [Использование технологии IntelliSense](../ide/using-intellisense.md).

## <a name="whats-new-in-the-javascript-language-service-in-visual-studio-2017"></a>Новые возможности JavaScript Language Service в Visual Studio 2017

Начиная с Visual Studio 2017 JavaScript IntelliSense отображает гораздо больше информации в списках членов и параметров. Эта новая информация предоставляется языковой службой TypeScript, которая использует статический анализ, чтобы помочь вам лучше понять код.

Для формирования такой информации TypeScript использует несколько источников.

- [IntelliSense на основе определения типа](#TypeInference)
- [IntelliSense на основе JSDoc](#JsDoc)
- [IntelliSense на основе файлов объявления TypeScript](#TsDeclFiles)
- [Автоматическое получение определений типов](#Auto)

<a name="TypeInference"></a>

### <a name="intellisense-based-on-type-inference"></a>IntelliSense на основе определения типа

В большинстве случаев явные сведения о типах в JavaScript недоступны. Но тип обычно довольно легко вывести из контекста кода.
Этот процесс называется определением типа.

Для переменной или свойства типом обычно является тип значения, используемый для его инициализации, либо последнее присвоенное значение.

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Для функции тип возвращаемого значения можно вывести из операторов return.

Для параметров функций вывод сейчас отсутствует, однако это можно обойти с помощью файлов *.d.ts* TypeScript или JSDoc (см. в следующих разделах).

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

<a name="JsDoc"></a>

### <a name="intellisense-based-on-jsdoc"></a>IntelliSense на основе JSDoc

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

Сведения о поддерживаемых сейчас заметках JsDoc см. в разделе [Поддержка JSDoc в JavaScript](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript).

<a name="TsDeclFiles"></a>
### <a name="intellisense-based-on-typescript-declaration-files"></a>IntelliSense на основе файлов объявления TypeScript

Так как JavaScript и TypeScript теперь основаны одной языковой службе, они способны полнее взаимодействовать друг с другом. Например, JavaScript IntelliSense можно предоставить для значений, объявленных в файле *.d.ts* (см. [документацию по TypeScript](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)), а типы, такие как интерфейсы и классы, объявленные в TypeScript, доступны для использования в качестве типов в комментариях JsDoc.

Ниже показан простой пример файла определения TypeScript, предоставляющий подробные сведения о типе (через интерфейс) файлу JavaScript в том же проекте (с помощью тега `JsDoc`).

![Файл определения TypeScript](https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png)

<a name="Auto"></a>
### <a name="automatic-acquisition-of-type-definitions"></a>Автоматическое получение определений типов

В среде TypeScript API наиболее популярных библиотек JavaScript описываются файлами *.d.ts*, а наиболее распространенным репозиторием для таких определений является [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

По умолчанию языковая служба языка сальса будет пытаться определить используемые библиотеки JavaScript, а затем автоматически скачать и указать в ссылке соответствующий файл *.d.ts*, описывающий эту библиотеку, чтобы расширить возможности IntelliSense. Файлы скачиваются в кэш, расположенный в пользовательской папке в *%LOCALAPPDATA%\Microsoft\TypeScript*.

> [!NOTE]
> Эта функция **отключена** по умолчанию при использовании файла конфигурации *tsconfig.json*, но ее можно включить, воспользовавшись описанием ниже.

Сейчас автоматическое определение работает для зависимостей, скачанных из npm (путем чтения файла *package.json*), Bower (путем чтения файла *bower.json*) и свободных файлов в проекте, которые примерно соответствуют списку из 400 наиболее популярных библиотек JavaScript. Например, если у вас в проекте есть *jquery-1.10.min.js*, для расширения возможностей редактирования будет получен и загружен файл *jquery.d.ts*. Этот файл *.d.ts* не оказывает влияния на проект.

Если вы не хотите использовать автоматическое получение, отключите его, добавив указанный ниже файл конфигурации. Вы по-прежнему можете вручную поместить файлы определений для использования непосредственно в проекте.

## <a name="see-also"></a>См. также раздел

- [Использование технологии IntelliSense](../ide/using-intellisense.md)
- [Поддержка по JavaScript (Visual Studio для Mac)](/visualstudio/mac/javascript)
