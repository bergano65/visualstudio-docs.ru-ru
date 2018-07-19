---
title: Практическое руководство. Распространение фрагментов кода
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 85500cfb5d8977c1e06ac925a44ba20bf3144d31
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280329"
---
# <a name="how-to-distribute-code-snippets"></a>Практическое руководство. Распространение фрагментов кода

Фрагменты кода можно передать другим пользователям для установки на других компьютерах с помощью диспетчера фрагментов кода. Однако если нужно распространить несколько фрагментов или распространить фрагмент более широко, файл фрагмента можно включить в расширение Visual Studio, которое могут установить пользователи Visual Studio.

Для создания расширений Visual Studio необходимо установить пакет Visual Studio SDK. Найти версию пакета VSSDK, соответствующую вашей версии Visual Studio, можно на странице [Файлы Visual Studio для скачивания](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

## <a name="set-up-the-extension"></a>Настройка расширения

В этой процедуре будет использоваться фрагмент кода Hello World, созданный в статье [Пошаговое руководство. Создание фрагмента кода](../ide/walkthrough-creating-a-code-snippet.md). Текст файла *SNIPPET* будет предоставлен, так что вам не придется возвращаться к этому разделу.

1.  Создайте проект VSIX с именем **TestSnippet**. (**Файл** > **Создать** > **Проект** > **Visual C# (Visual Basic)** > **Расширение среды**.)

2.  Добавьте в проект **TestSnippet** новый XML-файл и присвойте ему имя *VBCodeSnippet.snippet*. Замените содержимое файла следующим кодом:

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

1.  В **обозревателе решений** выберите узел проекта и добавьте папку с именем, которое должен иметь фрагмент в **диспетчере фрагментов кода**. В этом случае это имя **HelloWorldVB**.

2.  Переместите файл *SNIPPET* в папку *HelloWorldVB*.

3.  Выберите файл *SNIPPET* в **обозревателе решений** и установите в окне **Свойства** для свойства **Действие сборки** значение **Содержимое**, для свойства **Копировать в выходной каталог** — значение **Всегда копировать**, а для свойства **Включить в VSIX** — значение **true**.

### <a name="add-the-pkgdef-file"></a>Добавление файла PKGDEF

1.  Добавьте в папку *HelloWorldVB* текстовый файл и присвойте ему имя *HelloWorldVB.pkgdef*. Этот файл служит для добавления ряда разделов в реестр. В этом случае он добавляет новый подраздел в следующий раздел:

     `HKCU\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic`

2.  Добавьте в файл указанные ниже строки.

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Если изучить содержимое этого раздела, то можно понять, как указывать разные языки.

3.  Выберите файл *PKGDEF* в **обозревателе решений** и установите в окне **Свойства** для свойства **Действие сборки** значение **Содержимое**, для свойства **Копировать в выходной каталог** — значение **Всегда копировать**, а для свойства **Включить в VSIX** — значение **true**.

4.  Добавьте файл *PKGDEF* в качестве ресурса в манифест VSIX. В файле *source.extension.vsixmanifest* перейдите на вкладку **Активы** и нажмите **Создать**.

5.  В диалоговом окне **Добавить новый актив** выберите для параметра **Тип** значение **Microsoft.VisualStudio.VsPackage**, для параметра **Источник** — значение **Файл в файловой системе**, а для параметра **Путь** — значение **HelloWorldVB.pkgdef** (выберите его в раскрывающемся списке).

### <a name="test-the-snippet"></a>Тестирование фрагмента кода

1.  Теперь можно проверить, правильно ли работает фрагмент, в экспериментальном экземпляре Visual Studio. Экспериментальный экземпляр — это вторая копия Visual Studio, отличная от той, в которой вы пишете код. Он позволяет работать с расширением, не оказывая влияния на среду разработки.

2.  Выполните сборку решения и запустите отладку. Откроется второй экземпляр Visual Studio.

3.  В экспериментальном экземпляре выберите **Сервис > Диспетчер фрагментов кода** и выберите для параметра **Язык** значение **Basic**. В списке папок должна быть папка *HelloWorldVB*, развернув которую, можно увидеть фрагмент кода *HelloWorldVB*.

4.  Протестируйте фрагмент кода. В экспериментальном экземпляре откройте проект Visual Basic, а затем откройте один из файлов кода. Поместите курсор где-либо в коде, щелкните правой кнопкой мыши и в контекстном меню выберите пункт **Вставить фрагмент**.

5.  В списке папок должна быть папка *HelloWorldVB*. Дважды щелкните его. Должно появиться всплывающее окно **Вставить фрагмент: HelloWorldVB >** с раскрывающимся списком **HelloWorldVB**. Откройте раскрывающийся список **HelloWorldVB**. В файл должна добавиться следующая строка:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>См. также

- [Фрагменты кода](../ide/code-snippets.md)