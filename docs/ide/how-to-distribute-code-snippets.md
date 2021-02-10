---
title: Распространение фрагментов кода в качестве расширения
description: Сведения о том, как с помощью диспетчера фрагментов кода выполнить распределение фрагментов между другими разработчиками.
ms.custom: SEO-VS-2020
ms.date: 03/21/2019
ms.topic: how-to
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 65b60eb1156fe3d64081724e310a41a38b54af50
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969819"
---
# <a name="how-to-distribute-code-snippets"></a>Практическое руководство. Распространение фрагментов кода

Фрагменты кода можно передать другим пользователям для установки на других компьютерах с помощью **диспетчера фрагментов кода**. Однако если нужно распространить несколько фрагментов или распространить фрагмент более широко, файл фрагмента можно включить в расширение Visual Studio. Пользователи Visual Studio могут установить это расширение, чтобы получить фрагменты кода.

## <a name="prerequisites"></a>Предварительные требования

Установите рабочую нагрузку **Разработка расширений Visual Studio**, чтобы получить доступ к шаблонам проектов **Проект VSIX**.

![Рабочая нагрузка "Разработка расширений Visual Studio"](media/vs-2019/extension-development-workload.png)

## <a name="set-up-the-extension"></a>Настройка расширения

В этой процедуре будет использоваться фрагмент кода Hello World, созданный в статье [Пошаговое руководство. создание фрагмента кода](../ide/walkthrough-creating-a-code-snippet.md). Эта статья содержит XML-код фрагмента, поэтому вам не придется возвращаться и создавать его.

1. Создайте проект из шаблона **Пустой проект VSIX** и назовите его **TestSnippet**.

2. Добавьте в проект **TestSnippet** новый XML-файл и присвойте ему имя *VBCodeSnippet.snippet*. Замените содержимое следующим кодом XML:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <CodeSnippets
        xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
      <CodeSnippet Format="1.0.0">
        <Header>
          <Title>Hello World VB</Title>
          <Shortcut>HelloWorld</Shortcut>
          <Description>Inserts code</Description>
          <Author>MSIT</Author>
          <SnippetTypes>
            <SnippetType>Expansion</SnippetType>
            <SnippetType>SurroundsWith</SnippetType>
          </SnippetTypes>
        </Header>
        <Snippet>
          <Code Language="VB">
            <![CDATA[Console.WriteLine("Hello, World!")]]>
          </Code>
        </Snippet>
      </CodeSnippet>
    </CodeSnippets>
    ```

### <a name="set-up-the-directory-structure"></a>Настройка структуры каталогов

1. В **обозревателе решений** выберите узел проекта и добавьте папку с именем, которое должен иметь фрагмент в **диспетчере фрагментов кода**. В этом случае это имя **HelloWorldVB**.

2. Переместите файл *SNIPPET* в папку *HelloWorldVB*.

3. Выберите файл *SNIPPET* в **обозревателе решений** и установите в окне **Свойства** для свойства **Действие сборки** значение **Содержимое**, для свойства **Копировать в выходной каталог** — значение **Всегда копировать**, а для свойства **Включить в VSIX** — значение **true**.

### <a name="add-the-pkgdef-file"></a>Добавление файла PKGDEF

::: moniker range="vs-2017"

1. Добавьте в папку *HelloWorldVB* текстовый файл и присвойте ему имя *HelloWorldVB.pkgdef*. Этот файл служит для добавления ряда разделов в реестр. В этом случае новый подраздел добавляется в раздел **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Добавьте в папку *HelloWorldVB* текстовый файл и присвойте ему имя *HelloWorldVB.pkgdef*. Этот файл служит для добавления ряда разделов в реестр. В этом случае новый подраздел добавляется в раздел **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Languages\CodeExpansions\Basic**.

::: moniker-end

2. Добавьте в файл указанные ниже строки.

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Если изучить содержимое этого раздела, то можно понять, как указывать разные языки.

3. Выберите в **обозревателе решений** файл *PKGDEF* и в окне **Свойства** проследите за тем, чтобы были заданы следующие свойства:

   - **Действие сборки** — **Содержимое**;
   - **Копировать в выходной каталог** — **Всегда копировать**;
   - **Включить в VSIX** — **true**.

4. Добавьте файл *PKGDEF* в качестве ресурса в манифест VSIX. В файле *source.extension.vsixmanifest* перейдите на вкладку **Активы** и нажмите **Создать**.

5. В диалоговом окне **Добавить новый актив** выберите для параметра **Тип** значение **Microsoft.VisualStudio.VsPackage**, для параметра **Источник** — значение **Файл в файловой системе**, а для параметра **Путь** — значение **HelloWorldVB.pkgdef** (выберите его в раскрывающемся списке).

### <a name="test-the-snippet"></a>Тестирование фрагмента кода

1. Теперь можно проверить, правильно ли работает фрагмент, в экспериментальном экземпляре Visual Studio. Экспериментальный экземпляр — это вторая копия Visual Studio, отличная от той, в которой вы пишете код. Он позволяет работать с расширением, не оказывая влияния на среду разработки.

2. Выполните сборку решения и запустите отладку.

   Откроется второй экземпляр Visual Studio.

3. В экспериментальном экземпляре выберите **Сервис** > **Диспетчер фрагментов кода** и выберите для параметра **Язык** значение **Basic**. В списке папок должна быть папка *HelloWorldVB*, развернув которую, можно увидеть фрагмент кода *HelloWorldVB*.

4. Протестируйте фрагмент кода. В экспериментальном экземпляре откройте проект Visual Basic, а затем откройте один из файлов кода. Поместите курсор где-либо в коде, щелкните правой кнопкой мыши и в контекстном меню выберите пункт **Вставить фрагмент**.

5. В списке папок должна быть папка *HelloWorldVB*. Дважды щелкните его. Должно появиться всплывающее окно **Вставить фрагмент: HelloWorldVB >** с раскрывающимся списком **HelloWorldVB**. Откройте раскрывающийся список **HelloWorldVB**.

   В файл кода добавляется следующая строка:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>См. также

- [Фрагменты кода](../ide/code-snippets.md)
