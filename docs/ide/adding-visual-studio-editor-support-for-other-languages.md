---
title: Добавление поддержки редактора для других языков
description: Сведения о том, как редактор Visual Studio поддерживает возможности чтения и перемещения по разным языкам программирования и как можно добавить поддержку редактора для других языков.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax colorization
- IntelliSense
- IDE, navigation
- documents [Visual Studio], navigation
- TextMate bundle
- TextMate language grammar
- language support
ms.assetid: d78c43ee-4ef2-42e5-984e-d137de4e7e92
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5e78f632cdfe3e207e7ce71530d06c2a3b3fc6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914974"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Добавление поддержки редактора Visual Studio для других языков

Узнайте, каким образом редактор Visual Studio поддерживает возможности чтения и перемещения по разным языкам программирования и как можно добавить поддержку редактора Visual Studio для других языков.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Раскраска синтаксиса, завершение операторов и поддержка функции "Перейти к"

Доступные в редакторе Visual Studio функции, такие как раскраска синтаксиса, завершение операторов (также известная как IntelliSense) и _Перейти к_, упрощают написание, чтение и редактирование кода. На следующем снимке экрана показан пример редактирования скрипта Perl в Visual Studio. Синтаксис автоматически выделяется цветом. Например, примечания в коде выделяются зеленым цветом, код — черным, пути — красным, операторы — синим. Редактор Visual Studio автоматически применяет цветовое выделение синтаксиса к любому поддерживаемому им языку. Кроме того, по мере ввода известного ключевого слова или объекта функция завершения операторов выводит список возможных операторов и объектов. Функция завершения операторов упрощает написание кода.

![Раскраска синтаксиса в скрипте Perl](../ide/media/vside_perledit.png)

Сейчас Visual Studio поддерживает раскраску синтаксиса и завершение базовых операторов для следующих языков с помощью [грамматик TextMate](https://manual.macromates.com/en/language_grammars). Если предпочитаемый вами язык отсутствует в таблице, &mdash;его можно добавить.


- Bat
- F#
- Java
- Markdown
- Rust
- Visual Basic
- Clojure
- Go
- JavaDoc
- Objective-C
- ShaderLab
- C#
- CMake
- Groovy
- JSON
- Perl
- ShellScript
- Visual C++
- CoffeeScript
- HTML
- LESS
- Python
- SQL-код
- VBNet
- CSS
- INI
- LUA
- R
- Swift
- XML
- Docker
- Jade
- Производитель
- Ruby
- TypeScript
- YAML

Помимо раскраски синтаксиса и завершения основных операторов в Visual Studio также имеется функция [Перейти к](/archive/blogs/benwilli/visual-studio-tip-3-use-navigate-to). Она позволяет быстро выполнять поиск в файлах кода, путях к файлам и символах кода. Visual Studio предоставляет поддержку функции "Перейти к" для указанных далее языков.

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- Go

- Java

- PHP

Все эти типы файлов имеют описанные ранее функции, даже если поддержка для данного языка еще не была установлена. Установка специальной поддержки для некоторых языков может обеспечить дополнительную поддержку, например IntelliSense и другие расширенные языковые функции, такие как лампочки.

## <a name="add-support-for-non-supported-languages"></a>Добавление поддержки для неподдерживаемых языков

Visual Studio предоставляет языковую поддержку в редакторе с помощью [грамматики TextMate](https://manual.macromates.com/en/language_grammars). Если предпочитаемый вами язык программирования в настоящее время не поддерживается в редакторе Visual Studio, выполните поиск в Интернете. Пакет TextMate для этого языка уже может существовать. Если вы не можете найти пакет, добавьте для него поддержку самостоятельно, создав модель пакета TextMate для грамматики языка и фрагментов кода.

Добавьте новые грамматики TextMate для Visual Studio в следующую папку:

*%userprofile%\\.vs\Extensions*

По этому базовому пути добавьте следующие папки, если они применимы в вашем случае.

|Имя папки|Описание|
|-----------------|-----------------|
|\\*\<language name>*|Папка языка. Замените *\<language name>* именем языка. Например, *\Matlab*.|
|*\Syntaxes*|Папка грамматики. Содержит файлы *JSON* грамматики для языка, например *Matlab.json*.|
|*\Snippets*|Папка фрагментов кода. Содержит фрагменты кода для языка.|

В Windows *%userprofile%* разрешается в путь:  *C:\Users\\\<user name>* . Если в системе папки *Расширение* не существует, ее необходимо создать. Если папка уже существует, она будет скрыта.

> [!TIP]
> Если у вас есть файлы, открытые в редакторе, вам нужно закрыть и снова открыть их, чтобы увидеть выделение синтаксических конструкций после добавления грамматик TextMate.

Дополнительные сведения о создании грамматик TextMate см. в статьях [TextMate - Introduction to Language Grammars](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) (TextMate. Введение в грамматику языка) и [Notes on how to create a Language Grammar and Custom Theme for a Textmate Bundle](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle) (Заметки о создании грамматики языка и пользовательской темы для пакета Textmate).

## <a name="see-also"></a>См. также

- [Добавление расширения протокола языкового сервера](../extensibility/adding-an-lsp-extension.md)
- [Пошаговое руководство: создание фрагмента кода](../ide/walkthrough-creating-a-code-snippet.md)
- [Пошаговое руководство: отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md)
- [Пример кода: грамматика TextMate](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/TextmateGrammar)
- [Пример кода: поддержка пользовательского языка](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/Ook_Language_Integration)