---
title: Практическое руководство. Распространение фрагментов кода | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 14dea3842289b626b79d8dc7e294ba5f335d0351
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49185709"
---
# <a name="how-to-distribute-code-snippets"></a>Практическое руководство. Распространение фрагментов кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Фрагменты кода можно просто передать другим пользователям для установки на других компьютерах с помощью диспетчера фрагментов кода. Однако если нужно распространить несколько фрагментов или распространить фрагмент более широко, файл фрагмента можно включить в расширение Visual Studio, которое могут установить пользователи Visual Studio.  
  
 Для создания расширений Visual Studio необходимо установить пакет Visual Studio SDK. Найти версию VSSDK, соответствующую вашей версии Visual Studio [скачивания Visual Studio 2015](http://www.visualstudio.com/downloads/visual-studio-2015-downloads-vs.aspx).  
  
## <a name="setting-up-the-extension"></a>Настройка расширения  
 В этой процедуре будет использоваться фрагмент кода Hello World, созданный в разделе [Пошаговое руководство. Создание фрагмента кода](../ide/walkthrough-creating-a-code-snippet.md). Текст файла SNIPPET будет предоставлен, так что вам не придется возвращаться к этому разделу.  
  
1.  Создайте проект VSIX с именем **TestSnippet**. (**"Файл" > "Создать" > "Проект" > "Visual C#" (или "Visual Basic" > "Расширение среды"**)  
  
2.  Добавьте в проект **TestSnippet** новый XML-файл и присвойте ему имя **VBCodeSnippet.snippet**. Замените содержимое файла следующим кодом:  
  
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
  
#### <a name="setting-up-the-directory-structure"></a>Настройка структуры каталогов  
  
1.  В обозревателе решений выберите узел проекта и добавьте папку с именем, которое должен иметь фрагмент в диспетчере фрагментов кода. В этом случае это имя **HelloWorldVB**.  
  
2.  Переместите файл SNIPPET в папку **HelloWorldVB**.  
  
3.  Выберите файл SNIPPET в обозревателе решений и установите в окне **Свойства** для свойства **Действие сборки** значение **Содержимое**, для свойства **Копировать в выходной каталог** — значение **Всегда копировать**, а для свойства **Включить в VSIX** — значение **true**.  
  
#### <a name="adding-the-pkgdef-file"></a>Добавление файла PKGDEF  
  
1.  Добавьте в папку **HelloWorldVB** текстовый файл и присвойте ему имя **HelloWorldVB.pkgdef**. Этот файл служит для добавления ряда разделов в реестр. В этом случае он добавляет новый подраздел в раздел  
  
     **HKCU\Software\Microsoft\VisualStudio\14.0\Languages\CodeExpansions\Basic**.  
  
2.  Добавьте в файл указанные ниже строки.  
  
    ```  
    // Visual Basic   
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]   
    "HelloWorldVB"="$PackageFolder$"  
    ```  
  
     Если изучить содержимое этого раздела, то можно понять, как указывать разные языки.  
  
3.  Выберите файл PKGDEF в обозревателе решений и установите в окне **Свойства** для свойства **Действие сборки** значение **Содержимое**, для свойства **Копировать в выходной каталог** — значение **Всегда копировать**, а для свойства **Включить в VSIX** — значение **true**.  
  
4.  Добавьте файл PKGDEF в качестве ресурса в манифест VSIX. В файле source.extension.vsixmanifest перейдите на вкладку **Активы** и нажмите **Создать**.  
  
5.  В диалоговом окне **Добавить новый актив** выберите для параметра **Тип** значение **Microsoft.VisualStudio.VsPackage**, для параметра **Тип** — значение **Файл в файловой системе**, а для параметра **Путь** — значение **HelloWorldVB.pkgdef** (выберите его в раскрывающемся списке).  
  
### <a name="testing-the-snippet"></a>Тестирование фрагмента  
  
1.  Теперь можно проверить, правильно ли работает фрагмент, в экспериментальном экземпляре Visual Studio. Экспериментальный экземпляр — это вторая копия Visual Studio, отличная от той, в которой вы пишете код. Он позволяет работать с расширением, не оказывая влияния на среду разработки.  
  
2.  Выполните сборку решения и запустите отладку. Откроется второй экземпляр Visual Studio.  
  
3.  В экспериментальном экземпляре выберите **"Сервис" > "Диспетчер фрагментов кода"** и выберите для параметра **Язык** значение **Basic**. В списке папок должна быть папка HelloWorldVB, развернув которую, можно увидеть фрагмент кода HelloWorldVB.  
  
4.  Протестируйте фрагмент кода. В экспериментальном экземпляре откройте проект Visual Basic, а затем откройте один из файлов кода. Поместите курсор где-либо в коде, щелкните правой кнопкой мыши и в контекстном меню выберите пункт **Вставить фрагмент**.  
  
5.  В списке папок должна быть папка HelloWorldVB. Дважды щелкните его. Должно появиться всплывающее окно **Вставить фрагмент: HellowWorldVB >** с раскрывающимся списком **HelloWorldVB**. Откройте раскрывающийся список HelloWorldVB. В файл должна добавиться следующая строка:  
  
    ```vb  
    Console.WriteLine("Hello, World!")  
    ```  
  
## <a name="see-also"></a>См. также  
 [Фрагменты кода](../ide/code-snippets.md)



