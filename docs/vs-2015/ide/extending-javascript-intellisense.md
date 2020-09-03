---
title: Расширение IntelliSense для JavaScript | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- JavaScript, intellisense object
- extending JavaScript IntelliSense
- customizing JavaScript IntelliSense
- JavaScript, extending IntelliSense
- IntelliSense [JavaScript], extending
ms.assetid: 004e1ab6-bd7a-4327-9e01-89b9be96ba2f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf16b6fdc307e11875f30cfad6e4bb35580b0b04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665751"
---
# <a name="extending-javascript-intellisense"></a>Расширение IntelliSense для JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Функция расширяемости JavaScript IntelliSense позволяет настраивать результаты IntelliSense в редакторе JavaScript для библиотек сторонних производителей. Это может улучшить работу разработчиков, использующих эти библиотеки.

 Языковая служба JavaScript предоставляет возможности IntelliSense для сторонних библиотек JavaScript, которые добавляются в проект. Для большинства библиотек завершение операторов предоставляется автоматически языковой службой. На следующем рисунке показан пример завершения операторов.

 ![Пример завершения операторов](../ide/media/js-intellisense-completion.png "js_intellisense_completion")

 Если в библиотеку входят описания переменных, функций и объектов в стандартных тегах комментариев JavaScript (//), то по умолчанию в функции расширяемости IntelliSense автоматически выдается описательная информация, которая представляет собой всплывающую информацию, которая отображается справа от элементов в списке завершения, или при вводе открывающей скобки в вызове функции. Комментарии во всплывающем окне содержат описание элемента. В следующем примере показано всплывающее окно для списка завершения.

 ![Пример всплывающего окна "краткие сведения"&#45;](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")

 Для дальнейшего улучшения процесса разработки может потребоваться предоставить разработчикам сведения о типах во всплывающем окне. Сведения о типе можно указать с помощью [комментариев XML-документации](../ide/xml-documentation-comments-javascript.md) JavaScript вместо стандартных тегов комментариев. Комментарии к XML-документации добавляются с помощью тегов комментариев тройной косой черты (///) и определенного набора XML-элементов.

 Кроме того, можно предоставить сведения о типе с помощью расширяемости JavaScript IntelliSense. Эта функция позволяет настраивать результаты IntelliSense, создавая расширения JavaScript и добавляя их в контекст скрипта. В расширении, которое является файлом JavaScript, вы подписываетесь на события, предоставляемые `intellisense` объектом языковой службы. Расширяемость JavaScript IntelliSense является предпочтительным решением для библиотек, если шаблон поведения в библиотеке не позволяет языковой службе JavaScript предоставлять нужный уровень поддержки IntelliSense, а также требуется альтернатива декларативным комментариям XML-документации. Настроив результаты IntelliSense, можно создать интерфейс IntelliSense первого класса независимо от шаблонов поведения, которые могут ограничивать возможности языковой службы по умолчанию. См. подробнее о [завершении операторов для идентификаторов](../ide/statement-completion-for-identifiers.md).

## <a name="adding-an-extension-to-the-script-context"></a>Добавление расширения в контекст скрипта
 Для выполнения расширения IntelliSense его необходимо добавить в текущий контекст скрипта. Расширение можно автоматически добавить в контекст скрипта с помощью механизма автоматического обнаружения. также можно добавить расширение в контекст скрипта вручную с помощью групп ссылок или директивы Reference.

 Механизм автоматического обнаружения позволяет языковой службе автоматически находить расширения, которые следуют соглашению об именовании файлов *имябиблиотеки*.intellisense.js и находятся в том же каталоге, что и библиотека, к которой применяется расширение. Например, допустимое расширение библиотеки jQuery — jQuery.intellisense.js. Для более ограниченных расширений jQuery можно использовать имена файлов, такие как jQuery-1.7.1.intellisense.js (расширение для конкретной версии) или jQuery.ui.intellisense.js (расширение для библиотеки jQuery с областью видимости). Наиболее неопределенная версия расширения используется, если для данной библиотеки найдено более одного расширения.

 Если вы хотите использовать расширение для всех файлов проекта JavaScript, вы можете добавить расширение в группу ссылок. Существует несколько типов групп ссылок, которые включают неявные ссылки, и те, которые включают выделенные рабочие ссылки. Чтобы добавить расширение, обычно необходимо добавить файл в качестве неявной группы ссылок, неявного **(Windows)**, **неявного (Web)**. Неявные ссылки находятся в области действия для каждого JS файла, открытого в редакторе кода. При использовании этого метода необходимо добавить расширение и файл, который дополняет расширение.

 Используйте страницу **IntelliSense** диалогового окна **Параметры** , чтобы добавить расширение в качестве группы ссылок. Чтобы открыть страницу **IntelliSense** , выберите **Сервис**, **Параметры** в строке меню, а затем выберите **текстовый редактор**, **JavaScript**, **IntelliSense**, **ссылки**. Дополнительные сведения о группах ссылок см. в разделе [JavaScript IntelliSense](../ide/javascript-intellisense.md) и [Параметры, текстовый редактор, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

 Если вы хотите использовать расширение для определенного набора файлов, используйте директиву Reference. При использовании этого метода необходимо ссылаться как на расширение, так и на файл, дополненный расширением. Дополнительные сведения об использовании директивы Reference см. в разделе [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="handling-intellisense-events"></a>Обработка событий IntelliSense
 Функция расширяемости позволяет настраивать результаты IntelliSense с помощью подписки на события, такие как `statementcompletion` событие объекта языковой службы `intellisense` . В следующем примере показано простое расширение, которое используется языковой службой для скрытия элементов, начинающихся с символа подчеркивания от завершения операторов. Этот код содержится в underscorefilter.js и находится в \\ \\ папке \жаваскрипт\референцес *пути установки Visual Studio*.

```javascript
intellisense.addEventListener('statementcompletion', function (event) {
    if (event.targetName === "this") return;

    var filterRegex;

    if (event.target === undefined || event.target === window)
        filterRegex = /^_.*\d{2,}/;
    else
        filterRegex = /^_.*/;

    event.items = event.items.filter(function (item) {
        return !filterRegex.test(item.name);
    });
});
```

 В приведенном выше коде расширение проверяет [свойство TargetName](#TargetName) и свойства [целевого свойства](#Target) `statementcompletion` объекта события, чтобы исключить объекты, такие как `this` и `window` , и убедиться, что можно определить допустимый список завершения операторов. Если можно определить список завершения, расширение обновляет коллекцию [свойств элементов](#Items) завершения операторов путем фильтрации членов, начинающихся с символа подчеркивания.

 Дополнительные примеры см \\ \\ . в папке \жаваскрипт\референцес *путь установки Visual Studio*. Файл showPlainComments.js в этой папке содержит примеры использования других событий для обеспечения поддержки IntelliSense по умолчанию для стандартных тегов комментариев JavaScript (//). Как и underscorefilter.js, showPlainComments.js уже доступен в качестве рабочего расширения, а полученные данные IntelliSense можно просмотреть при использовании тегов комментариев в коде для переменных, функций и объектов. Дополнительные примеры см. в разделе [примеры кода](#CodeExamples).

> [!WARNING]
> При изменении файлов расширений, включенных в Visual Studio, можно отключить JavaScript IntelliSense или функцию, поддерживаемую расширением.

 В коде расширения можно создавать обработчики для следующих типов событий с помощью `addEventListener` :

- `statementcompletion`, который добавляет обработчик для события завершения инструкции. Завершение операторов предоставляет список элементов для определенного типа, который появляется после ввода специального символа, например точки (.), или списка идентификаторов, которые появляются при вводе или нажатии клавиш CTRL + J. Обработчик получает объект события типа `CompletionEvent` , который поддерживает следующие члены: [свойства элементов](#Items), [целевое свойство](#Target), [свойство TargetName](#TargetName)и [свойство Scope](#Scope).

- `signaturehelp`, который добавляет обработчик для сведений о параметрах IntelliSense. Сведения о параметрах предоставляют сведения о количестве, именах и типах параметров, необходимых для функции. Обработчик получает объект события типа `SignatureHelpEvent` , который поддерживает следующие члены: [свойство Target](#Target), [свойство ParentObject](#ParentObject), свойство [функтионкомментс](#FunctionComments), [свойство функтионхелп](#FunctionHelp).

- `statementcompletionhint`, который добавляет обработчик для быстрой информации IntelliSense. Во всплывающем окне краткие сведения отображается полное объявление идентификаторов в коде. Обработчик получает объект события типа `CompletionHintEvent` , который поддерживает следующие члены: [свойство Комплетионитем](#CompletionItem)и [свойство симболхелп](#SymbolHelp).

  Примеры, в которых демонстрируются функции IntelliSense, такие как завершение операторов, сведения о параметрах и краткие сведения, см. [в разделе Использование IntelliSense](../ide/using-intellisense.md).

> [!NOTE]
> В JavaScript краткие сведения — это всплывающее окно, которое отображается справа от списка завершения. Краткие сведения нельзя вызывать вручную.

## <a name="intellisense-object"></a><a name="intellisenseObject"></a> Объект IntelliSense
 В следующей таблице показаны функции, доступные для `intellisense` объекта. `intellisense`Объект доступен только во время разработки.

|Компонент|Описание|
|--------------|-----------------|
|`addEventListener(type, handler);`|Добавляет обработчик событий для события IntelliSense.<br /><br /> `type` Строковое значение. Допустимыми значениями являются `statementcompletion`, `signaturehelp` и `statementcompletionhint`.<br /><br /> `handler` — Это функция обработчика событий, которая получает объект события одного из следующих типов:<br /><br /> -   `CompletionEvent`, используемый для `statementcompletion` события.<br />-   `SignatureHelpEvent`, используемый для `signaturehelp` события.<br />-   `CompletionHintEvent`, используемый для `statementcompletionhint` события.<br /><br /> Примеры использования этой функции см. в разделе [примеры кода](#CodeExamples).|
|`annotate(obj, doc);`|Указывает документацию для объекта путем копирования комментариев документации из одного объекта в другой объект.<br /><br /> `obj` Указывает объект, в который необходимо скопировать документацию.<br /><br /> `doc` Указывает объект, из которого необходимо скопировать документацию.<br /><br /> Пример использования этой функции см. в разделе [Добавление заметок IntelliSense](#Annotations).|
|`getFunctionComments(func);`|Возвращает комментарии для указанной функции.<br /><br /> `func` Указывает функцию, для которой возвращаются комментарии.<br /><br /> Параметр можно задать с `func` помощью `completionItem.value` .<br /><br /> Возвращаемый `functionComments` объект содержит следующие члены: `above` , `inside` и `paramComment` . Дополнительные сведения см. в описании свойства [Функтионкомментс свойства](#FunctionComments) .<br /><br /> `getFunctionComments` может вызываться только в одном из обработчиков событий, зарегистрированных в `addEventListener` .<br /><br /> Пример использования этой функции см. в разделе \\ \\ *путь установки Visual Studio*\JavaScript\References\showPlainComments.js.|
|`logMessage(msg);`|Отправляет диагностические сообщения в окно вывода.<br /><br /> `msg` Строка, содержащая сообщение.<br /><br /> Пример использования этой функции см. в разделе [Отправка сообщений в окно вывода](#Logging).|
|`nullWithCompletionsOf(value);`|Возвращает специальное значение null, для которого список завершения определяется объектом, переданным в `value` параметре.<br /><br /> `value` Определяет список завершения для возвращаемого значения. `value` может быть любым типом.<br /><br /> Возвращаемое значение NULL обрабатывается как значение null во время разработки, но список завершения для возвращаемого значения совпадает со списком завершения для `value` параметра.<br /><br /> Одна из них — предоставить IntelliSense для возвращаемого значения, если возвращаемый тип предсказуем во время выполнения, но возвращаемое значение — `null` во время разработки.|
|`redirectDefinition(func, definition);`|Указывает IntelliSense использовать предоставленную функцию определения вместо первоначальной функции func при запросе параметра Help или **Go To Definition** .<br /><br /> `func` Задает целевую функцию.<br /><br /> `definition` Задает функцию, используемую вместо целевой функции для сведений о параметрах и **перехода к определению**.|
|`setCallContext(func, thisArg);`|Задает контекст вызова или область для указанной функции.<br /><br /> `func` Задает функцию, для которой задается область.<br /><br /> `thisArg` Объектный литерал, на который `this` может ссылаться ключевое слово, который указывает новую область для элемента. Можно включить аргументы для передачи в этот параметр, например `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` предоставляет поведение, аналогичное `Function.prototype.bind` , за исключением того, что оно использовалось только для поддержки технологии IntelliSense во время разработки. Можно использовать `setCallContext` для задания области действия функции, если необходимо имитировать вызов кода, который в противном случае недостижим, поэтому при вызове функции в вызове функции будут включены правильные область и аргументы.|
|`undefinedWithCompletionsOf(value);`|Возвращает особое неопределенное значение, для которого список завершения определяется объектом, переданным в `value` параметре.<br /><br /> `value` Определяет список завершения для возвращаемого значения. `value` может быть любым типом.<br /><br /> Неопределенное возвращаемое значение рассматривается как неопределенное во время разработки, но список завершения для возвращаемого значения совпадает со списком завершения для `value` параметра.<br /><br /> Одна из них — предоставить IntelliSense для возвращаемого значения, если возвращаемый тип во время выполнения является прогнозируемым, но возвращаемое значение не определено на этапе разработки.|
|`version()`|Возвращает версию Visual Studio.|

## <a name="event-members"></a>Члены события
 В следующих разделах описываются элементы, которые предоставляются в объекте события для следующих событий: `statementcompletion` , `signaturehelp` и `statementcompletionhint` .

### <a name="completionitem-property"></a><a name="CompletionItem"></a> Комплетионитем, свойство
 Возвращает идентификатор, известный как элемент завершения, для которого запрашивается всплывающее окно кратких сведений. Это свойство доступно для `statementcompletionhint` объекта события и для свойства [Items](#Items) `statementcompletion` объекта события.

 Возвращаемое значение: `completionItem` объект

 Ниже перечислены члены `completionItem` объекта.

- `name`. Чтение и запись при использовании в `items` коллекции; в противном случае — только для чтения. Возвращает строку, определяющую элемент завершения.

- `kind`. Чтение и запись при использовании в `items` коллекции; в противном случае — только для чтения. Возвращает строку, представляющую тип элемента завершения. Возможные значения: метод, поле, свойство, параметр, переменная и зарезервировано.

- `glyph`. Чтение и запись при использовании в `items` коллекции; в противном случае — только для чтения. Возвращает строку, которая представляет значок, отображаемый в списке завершения. Возможные значения для `glyph` использования следующего формата: VS:*глифтипе*, где *глифтипе* соответствует элементам, не зависящим от языка, в <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> перечислении. Например, `vs:GlyphGroupMethod` может иметь одно возможное значение для `glyph` . Если `glyph` не задано, `kind` свойство определяет значок по умолчанию.

- `parentObject`. Только для чтения. Возвращает родительский объект.

- `value`. Только для чтения. Возвращает объект, представляющий значение элемента завершения.

- `comments`. Только для чтения. Возвращает строку, содержащую комментарии, которые находятся над полем или переменной.

- `scope`. Только для чтения. Возвращает область элемента завершения. Возможные значения: Global, Local, Parameter и Member.

### <a name="items-property"></a><a name="Items"></a> элемент, свойство
 Возвращает или задает массив элементов завершения операторов. Каждый элемент массива является объектом [Свойства комплетионитем](#CompletionItem) . `items`Свойство доступно для `statementcompletion` объекта события.

 Возвращаемое значение: массив

### <a name="functioncomments-property"></a><a name="FunctionComments"></a> Функтионкомментс, свойство
 Возвращает комментарии для функции. Это свойство доступно для `signaturehelp` объекта события.

 Возвращаемое значение: `comments` объект

 Ниже перечислены члены `comments` объекта.

- `above`. Возвращает комментарии над функцией.

- `inside`. Возвращает комментарии внутри функции, обычно в формате Всдок.

- `paramComments`. Возвращает массив, представляющий комментарии для каждого параметра в функции. Члены массива включают:

  - `name`. Возвращает строку, представляющую имя параметра.

  - `comment`. Возвращает строку, содержащую комментарий к параметру.

### <a name="functionhelp-property"></a><a name="FunctionHelp"></a> Функтионхелп, свойство
 Возвращает справку для функции. Это свойство доступно для `signaturehelp` объекта события.

 Возвращаемое значение: `functionHelp` объект

 Ниже перечислены члены `functionHelp` объекта.

- `functionName`. Read/write. Возвращает строку, содержащую имя функции.

- `signatures`. Read/write. Возвращает или задает массив сигнатур функций. Каждый элемент массива является `signature` объектом. Некоторые `signature` свойства, такие как `locid` , соответствуют общим атрибутам [комментариев XML-документации](../ide/xml-documentation-comments-javascript.md) .

  К членам `signature` объекта относятся:

  - `description`. Read/write. Возвращает строку, описывающую функцию.

  - `locid`. Read/write. Возвращает идентификатор строки, содержащий сведения о локализации функции.

  - `helpKeyword`. Read/write. Возвращает строку, содержащую ключевое слово справки.

  - `externalFile`. Read/write. Возвращает строку, которая представляет файл, содержащий идентификатор элемента.

  - `externalid`. Read/write. Возвращает строку, представляющую идентификатор элемента функции.

  - `params`. Read/write. Возвращает или задает массив параметров для функции. Каждый элемент в массиве параметров — это `parameter` объект со свойствами, которые соответствуют следующим атрибутам [\<param>](../ide/param-javascript.md) элемента:

    - `name`. Read/write. Возвращает строку, представляющую имя параметра.

    - `type`. Read/write. Возвращает строку, представляющую тип параметра.

    - `elementType`. Read/write. Если тип — `Array` , возвращает строку, представляющую тип элементов в массиве.

    - `description`. Read/write. Возвращает строку, описывающую параметр.

    - `locid`. Read/write. Возвращает идентификатор строки, содержащий сведения о локализации функции.

    - `optional`. Read/write. Возвращает строку, которая указывает, является ли параметр необязательным. `true` Указывает, что параметр является необязательным; `false` указывает, что это не так.

  - `returnValue`. Read/write. Возвращает или задает объект возвращаемого значения со свойствами, которые соответствуют следующим атрибутам [\<returns>](../ide/returns-javascript.md) элемента:

    - `type`. Read/write. Возвращает строку, представляющую тип возвращаемого значения.

    - `elementType`. Read/write. Если тип — `Array` , возвращает строку, представляющую тип элементов в массиве.

    - `description`. Read/write. Возвращает строку, описывающую возвращаемое значение.

    - `locid`. Read/write. Возвращает идентификатор строки, содержащий сведения о локализации функции.

    - `helpKeyword`. Read/write. Возвращает строку, содержащую ключевое слово справки.

    - `externalFile`. Read/write. Возвращает строку, которая представляет файл, содержащий идентификатор элемента.

    - `externalid`. Read/write. Возвращает строку, представляющую идентификатор элемента функции.

### <a name="parentobject-property"></a><a name="ParentObject"></a> parentObject, свойство
 Возвращает родительский объект функции-члена. Например, для `document.getElementByID` `parentObject` возвращает `document` объект. Это свойство доступно для `signaturehelp` объекта события.

 Возвращаемое значение: объект

### <a name="target-property"></a><a name="Target"></a> целевое свойство
 Возвращает объект, представляющий элемент слева от символа триггера, который представляет собой точку (.). Для функций `target` возвращает функцию, для которой запрашиваются сведения о параметрах. Это свойство доступно для `statementcompletion` `signaturehelp` объектов событий и.

 Возвращаемое значение: объект

### <a name="targetname-property"></a><a name="TargetName"></a> Свойство targetName
 Возвращает строку, представляющую целевой объект. Например, для "this." `targetName` возвращает "this". Для "A. B" (если курсор находится после "B"), `targetName` возвращает "b". Это свойство доступно для `statementcompletion` объекта события.

 Возвращаемое значение: строка

### <a name="symbolhelp-property"></a><a name="SymbolHelp"></a> Симболхелп, свойство
 Возвращает элемент завершения, для которого запрашивается всплывающее окно кратких сведений. Это свойство доступно для `statementcompletionhint` объекта события.

 Возвращаемое значение: `symbolHelp` Object.

 Некоторые свойства `symbolHelp` объекта, такие как `locid` , соответствуют общим атрибутам [комментариев XML-документации](../ide/xml-documentation-comments-javascript.md) .

 Ниже перечислены члены `symbolHelp` объекта.

- `name`. Read/write. Возвращает строку, содержащую имя идентификатора.

- `symbolType`. Read/write. Возвращает строку, представляющую тип символа. Возможные значения: Unknown, Boolean, число, строка, объект, функция, массив, Дата и регулярное выражение.

- `symbolDisplayType`. Read/write. Возвращает строку, содержащую имя типа для вывода. Если `symbolDisplayType` параметр не задан, `symbolType` используется.

- `elementType`. Read/write. Если значение `symbolType` равно `Array` , возвращает строку, представляющую тип элементов в массиве.

- `scope`. Read/write. Возвращает строку, представляющую область символа. Возможные значения: Global, Local, Parameter и Member.

- `description`. Read/write. Возвращает строку, содержащую описание символа.

- `locid`. Read/write. Возвращает идентификатор строки, содержащий сведения о локализации символа.

- `helpKeyword`. Read/write. Возвращает строку, содержащую ключевое слово справки.

- `externalFile`. Read/write. Возвращает строку, которая представляет файл, содержащий идентификатор элемента.

- `externalid`. Read/write. Возвращает строку, представляющую идентификатор элемента символа.

- `functionHelp`. Read/write. Возвращает [свойство функтионхелп](#FunctionHelp), которое может содержать сведения, если `symbolType` функция имеет значение.

### <a name="scope-property"></a><a name="Scope"></a> scope, свойство
 Возвращает область выполнения события. Возможные значения для области выполнения — Global и Members. Это свойство доступно для `statementcompletion` объекта события.

 Возвращаемое значение: строка

## <a name="debugging-intellisense-extensions"></a>Отладка расширений IntelliSense
 Отладка расширений невозможна, но для отправки данных в окно вывода Visual Studio можно использовать функцию [объекта IntelliSense](#intellisenseObject) . Пример использования этой функции см. в разделе [Отправка сообщений в окно вывода](#Logging) далее в этом разделе. Для `logMessage` работы по крайней мере один обработчик событий должен быть зарегистрирован в расширении.

## <a name="code-examples"></a><a name="CodeExamples"></a> Примеры кода
 В этом разделе приводятся примеры кода, демонстрирующие использование API расширяемости IntelliSense. Существуют и другие способы использования этих API. Дополнительные примеры см. в следующих файлах в \\ \\ папке \жаваскрипт\референцес *пути установки Visual Studio*. Это рабочие примеры, используемые в языковой службе JavaScript.

- underscoreFilter.js. Этот код скрывает закрытые члены из IntelliSense. Он содержит обработчики событий для `statementcompletion` события.

- showPlainComments.js. Этот код обеспечивает поддержку IntelliSense для стандартных комментариев. Он содержит обработчики событий для `signaturehelp` `statementcompletionhint` событий и.

### <a name="adding-intellisense-annotations"></a><a name="Annotations"></a> Добавление аннотаций IntelliSense
 В следующей процедуре показано, как предоставить поддержку документации IntelliSense для библиотеки стороннего производителя, не изменяя библиотеку напрямую. Для этого можно использовать `intellisense.annotate` в расширении.

 Для работы этого примера в проекте необходимы следующие файлы JavaScript.

- demoLib.js — файл проекта, представляющий библиотеку стороннего разработчика.

- demoLib.intellisense.js, который является расширением IntelliSense. Этот файл не требуется включать в проект, но он должен находиться в той же папке, что и файл exampleLib.js.

- appCode.js — файл проекта, представляющий код приложения.

##### <a name="to-add-an-intellisense-annotation"></a>Добавление заметки IntelliSense

1. Добавьте следующий код для demoLib.js.

    ```javascript
    function someFunc(a) { };
    var rectangle;

    ```

2. Добавьте следующий код для demoLib.intellisense.js.

    ```javascript
    intellisense.annotate(someFunc, function (a) {
        /// <signature>
        /// <summary>Description of someFunc</summary>
        /// <param name="a">Param a</param>
        /// </signature>
    });

    intellisense.annotate(window, {
        // This is a comment on a global variable named rectangle.
        rectangle: undefined
    });
    ```

3. Добавьте следующую директиву ссылки в качестве первой строки в файле appCode.js. Использованный здесь путь указывает, что файлы JavaScript находятся в той же папке.

    ```javascript
    /// <reference path="demoLib.js" />

    ```

4. В appCode.js введите следующий код. Комментарии XML-документации отображаются в расширении в виде сведений о параметрах IntelliSense.

     ![Пример, демонстрирующий использование intellisense.annotate](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")

5. В appCode.js введите следующий код. При вводе вы увидите стандартные комментарии в расширении, отображаемом в виде кратких сведений IntelliSense.

     ![Пример, демонстрирующий использование intellisense.annotate](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")

### <a name="sending-messages-to-the-output-window"></a><a name="Logging"></a> Отправка сообщений в окно вывода
 Следующая процедура показывает, как отправить сообщения в окно вывода. Вы можете отправить сообщения, чтобы упростить отладку расширений IntelliSense.

 Для работы этого примера в проекте необходимы следующие файлы JavaScript.

- exampleLib.js — файл проекта, представляющий библиотеку стороннего разработчика.

- exampleLib.intellisense.js, который является расширением IntelliSense. Этот файл не требуется включать в проект, но он должен находиться в той же папке, что и файл exampleLib.js.

- appCode.js — файл проекта, представляющий код приложения.

##### <a name="to-send-a-message-to-the-output-window"></a>Отправка сообщения в окно вывода

1. Добавьте следующий код для exampleLib.js.

    ```javascript
    var someVar = {
        a: 1,
        b: 'hello'
    };
    ```

2. Добавьте следующий код для exampleLib.intellisense.js.

    ```javascript
    intellisense.addEventListener('statementcompletion', function (e) {
        // Prints out statement completion info: Either (1) the member
        // list, if the trigger character was typed, or (2) the
        // statement completion identifiers.
        // e.target represents the object left of the trigger character.
        intellisense.logMessage(
            e.target ? 'member list requested, target: ' + e.targetName : 'statement completion for current scope requested');

        // Prints out all statement completion items.
        e.items.forEach(function (item) {
            intellisense.logMessage('[completion item] ' + item.name + ', kind:' + item.kind + ', scope:' + item.scope + ', value:' + item.value);
        });
    });
    ```

3. Добавьте следующую директиву ссылки в качестве первой строки в файле appCode.js. Использованный здесь путь указывает, что файлы JavaScript находятся в той же папке.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

4. В окне Вывод выберите **JavaScript Language Service** в списке **Показывать выходные данные из** . (Чтобы просмотреть окно вывода, выберите **выходные данные** в меню Вид.)

5. В appCode.js введите следующий код. Во время ввода в окне вывода отображаются сообщения от языковой службы. Первое сообщение в окне Вывод указывает на то, что была запрошена завершение операторов для текущей области.

    ```javascript
    some
    ```

     Ниже приведено частичное представление выходных данных.

    ```scr
    03:16:14.3113: statement completion for current scope requested
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined

    …
    ```

6. Нажмите кнопку **Очистить все** в окне Вывод.

7. Введите следующий код. Первое сообщение в окне Вывод указывает на то, что был запрошен список элементов.

    ```javascript
    someVar.
    ```

     Ниже приведено частичное представление выходных данных.

    ```scr
    03:17:43.4032: member list requested, target: someVar
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:

    …
    ```

### <a name="changing-the-intellisense-icons"></a><a name="Icons"></a> Изменение значков IntelliSense
 В следующей процедуре показано, как изменить значки, отображаемые технологией IntelliSense по умолчанию. Это может быть полезно при предоставлении сведений IntelliSense о специфических для библиотеки понятиях, таких как пространства имен, классы, интерфейсы и перечисления.

 Сведения о доступных значениях значков см. в разделе <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> .

 Для работы этого примера в проекте необходимы следующие файлы JavaScript.

- exampleLib.js — файл проекта, репресенс библиотеку стороннего разработчика.

- exampleLib.intellisense.js, который является расширением IntelliSense. Этот файл не требуется включать в проект, но он должен находиться в той же папке, что и файл exampleLib.js.

- appCode.js — файл проекта, представляющий код приложения.

##### <a name="to-change-the-icons"></a>Изменение значков

1. Добавьте следующий код для exampleLib.js.

    ```javascript
    function Namespace(name) {
        this._isNamespace = true;
        window[name] = this;
    };

    function Enum(values) {
        var e = Object.create(values);
        e._isEnum = true;
        return e;
    };

    var SomeNamespace = new Namespace('SomeNamespace');
    // A constructor function is considered a class.
    SomeNamespace.SomeClass1 = function () { }
    SomeNamespace.Enum1 = new Enum({ VALUE1: 0, VALUE2: 1 });
    ```

2. Добавьте следующий код для exampleLib.intellisense.js.

    ```javascript
    intellisense.addEventListener('statementcompletion', function (e) {
        e.items.forEach(function (item) {
            // Detect a namespace by using the _isNamespace flag.
            if (item.value && item.value._isNamespace) {
                item.glyph = 'vs:GlyphGroupNamespace';
                }

            if (item.parentObject && item.parentObject._isNamespace) {
                // The item is a member of a namespace.

                // All constructor functions that are part of a namespace
                // are considered classes.
                // A constructor function starts with
                // an uppercase letter by convention.
                if (typeof item.value == 'function' && (item.name[0].toUpperCase()
                    == item.name[0])) {
                    item.glyph = 'vs:GlyphGroupClass';
                }

                // Detect an enumeration by using the _isEnum flag.
                if (item.value && item.value._isEnum) {
                    item.glyph = 'vs:GlyphGroupEnum';
                }
            }
        });
    });

    intellisense.addEventListener('statementcompletionhint', function (e) {
        if (e.completionItem.value) {
            if (e.completionItem.value._isNamespace) {
                e.symbolHelp.symbolDisplayType = 'Namespace';
            }
            if (e.completionItem.value._isEnum) {
                e.symbolHelp.symbolDisplayType = 'Enum';
            }
        }
    });
    ```

3. Добавьте следующую директиву ссылки в качестве первой строки в файле appCode.js. Использованный здесь путь указывает, что файлы JavaScript находятся в той же папке.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

4. В appCode.js введите следующий код. При вводе вы увидите, что значок для пространства имен изменился на " {} ", как используется в C#.

     ![Пример, демонстрирующий использование свойства glyph](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")

5. В appCode.js введите следующий код. При вводе вы увидите новый значок перечисления для элемента Enum1 и новый значок класса для элемента SomeClass1.

     ![Пример, демонстрирующий использование свойства glyph](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")

### <a name="avoiding-run-time-effects-on-intellisense-results"></a><a name="Overriding"></a> Предотвращение влияния на результаты выполнения IntelliSense при выполнении
 Языковая служба JavaScript запускает код для динамического предоставления информации IntelliSense. В результате поведение во время выполнения может иногда мешать желаемым результатам. В следующей процедуре показано, как переопределить результаты IntelliSense, когда поведение во время выполнения приводит к неверной технологии IntelliSense.

 Для работы этого примера в проекте необходимы следующие файлы JavaScript.

- exampleLib.js — файл проекта, представляющий библиотеку стороннего разработчика.

- exampleLib.intellisense.js, который является расширением IntelliSense. Этот файл не требуется включать в проект, но он должен находиться в той же папке, что и файл exampleLib.js.

- appCode.js — файл проекта, представляющий код приложения.

##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>Чтобы избежать последствий во время выполнения для результатов IntelliSense

1. Добавьте следующий код для exampleLib.js.

    ```javascript
    function after(count, func) {
        return function () {
            if (--times < 1) {
                return func.apply(this, arguments);
            }
        };
    };
    ```

     В приведенном выше коде функция с оболочкой пропускает начальные вызовы, основанные на значении `count` , и не возвращает результаты.

2. Добавьте следующую директиву ссылки в качестве первой строки в файле appCode.js. Использованный здесь путь указывает, что файлы JavaScript находятся в той же папке.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

3. В appCode.js введите следующий код. Вместо IntelliSense отображается список идентификаторов, поскольку функция с оболочкой не вызывается, а это означает, что `throttled` функция не возвращает никаких результатов.

     ![Пример переопределения результатов IntelliSense](../ide/media/js-intellisense-override.png "js_intellisense_override")

4. Добавьте следующий код для exampleLib.intellisense.js. Это изменит поведение во время разработки таким образом, чтобы функция IntelliSense отображалась для функции с оболочкой, как и ожидалось.

    ```javascript
    window.after = function (count, func) {
        // Just return func.
        return func;
    };
    ```

5. В appCode.js протестируйте результаты, введя тот же код, который был введен ранее. На этот раз IntelliSense предоставляет нужные сведения.

     ![Пример переопределения результатов IntelliSense](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")

## <a name="see-also"></a>См. также:
 Завершение операторов [JavaScript IntelliSense](../ide/javascript-intellisense.md) [для идентификаторов](../ide/statement-completion-for-identifiers.md)
