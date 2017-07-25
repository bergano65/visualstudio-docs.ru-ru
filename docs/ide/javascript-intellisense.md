---
title: "JavaScript IntelliSense | Документы Майкрософт"
ms.custom: 
ms.date: 06/28/2017
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
ms.translationtype: HT
ms.sourcegitcommit: 359e1eb5df8f19774d352ace631802367b6dd8c9
ms.openlocfilehash: 759ffc281b8c673f5987afc6512b225434b69dec
ms.contentlocale: ru-ru
ms.lasthandoff: 07/11/2017

---
# <a name="javascript-intellisense"></a>IntelliSense для JavaScript
[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] обеспечивает эффективное редактирование JavaScript. Система Visual Studio, основанная на языковой службе TypeScript, расширяет возможности IntelliSense, поддерживает современные компоненты JavaScript, а также улучшенные функции для повышения эффективности работы, такие как "Перейти к определению", рефакторинг и многое другое.

> [!NOTE]
>  Языковая служба JavaScript в [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] использует новый механизм языковой службы ("сальса"). Дополнительные сведения можно получить в этом разделе, а также в этой [записи блога](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/more-productive-javascript-in-visual-studio-2017-rc). Новые возможности редактирования в основном относятся к VS Code. Дополнительные сведения см. в [документах о VS Code](https://code.visualstudio.com/docs/languages/javascript).

Дополнительные сведения об общих функциональных возможностях IntelliSense в [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] см. в разделе [Использование технологии IntelliSense](../ide/using-intellisense.md). 

## <a name="whats-new-in-the-javascript-language-service-in-includevsdev15miscincludesvsdev15mdmd"></a>Новые возможности языковой службы JavaScript в [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

JavaScript IntelliSense в [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] теперь отображает гораздо больше информации в списках элементов и параметров.
Эта новая информация предоставляется языковой службой TypeScript, которая использует статический анализ, чтобы помочь вам лучше понять код.
Для формирования такой информации TypeScript использует несколько источников.
- [IntelliSense на основе определения типа](#TypeInference)
- [IntelliSense на основе JSDoc](#JsDoc)
- [IntelliSense на основе файлов объявления TypeScript](#TSDeclFiles)
- [Автоматическое получение определений типов](#Auto)

### <a name="TypeInference"></a>IntelliSense на основе определения типа
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

### <a name="JsDoc"></a> IntelliSense на основе JSDoc

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

### <a name="TsDeclFiles"></a> IntelliSense на основе файлов объявления TypeScript

Так как JavaScript и TypeScript теперь основаны одной языковой службе, они способны полнее взаимодействовать друг с другом. Например, JavaScript IntelliSense можно предоставить для значений, объявленных в файле `.d.ts` ([подробнее](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)), а типы, такие как интерфейсы и классы, объявленные в TypeScript, доступны для использования в качестве типов в комментариях JsDoc. 

Ниже показан простой пример файла определения TypeScript, предоставляющий подобные сведения о типе (через интерфейс) файлу JavaScript в том же проекте (с помощью тега JsDoc).

_**Объявления TypeScript, используемые в JavaScript**_

<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png" height="400" width="640"/>

### <a name="Auto"></a> Автоматическое получение определений типов
В среде TypeScript API наиболее популярных библиотек JavaScript описываются файлами `.d.ts`, а наиболее распространенным репозиторием для таких определений является [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

По умолчанию языковая служба языка сальса будет пытаться определить используемые библиотеки JavaScript, а затем автоматически скачать и указать в ссылке соответствующий файл `.d.ts`, описывающий эту библиотеку, чтобы расширить возможности IntelliSense. Файлы скачиваются в кэш, расположенный в пользовательской папке в `%LOCALAPPDATA%\Microsoft\TypeScript`. 

> [!NOTE]
> Эта функция **отключена** по умолчанию при использовании файла конфигурации `tsconfig.json`, но ее можно включить, воспользовавшись описанием ниже.

Сейчас автоматическое определение работает для зависимостей, скачанных из npm (путем чтения файла `package.json`), Bower (путем чтения файла `bower.json`) и свободных файлов в проекте, которые примерно соответствуют списку из 400 наиболее популярных библиотек JavaScript. Например, если у вас в проекте есть `jquery-1.10.min.js`, для расширения возможностей редактирования будет получен и загружен файл `jquery.d.ts`. Этот файл `.d.ts` не оказывает влияния на проект. 

Если вы не хотите использовать автоматическое получение, отключите его, добавив указанный ниже файл конфигурации. Вы по-прежнему можете вручную поместить файлы определений для использования непосредственно в проекте.



