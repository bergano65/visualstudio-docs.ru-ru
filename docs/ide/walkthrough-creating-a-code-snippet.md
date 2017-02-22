---
title: "Пошаговое руководство. Создание фрагмента кода | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "фрагменты кода, создание"
  - "фрагменты кода, импорт"
  - "фрагменты кода, ссылки"
  - "фрагменты кода, замены"
  - "фрагменты кода, ярлык"
  - "фрагменты кода, шаблон"
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Пошаговое руководство. Создание фрагмента кода
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно создать фрагмент кода только несколькими шагами.  Все, что необходимо сделать — создать XML\-файл, заполнить соответствующие элементы и добавить код к нему.  Можно также добавить ссылки и параметры замены в код.  Можно добавить фрагмент в папку установки Visual Studio с помощью кнопки импорта на диспетчере фрагментов кода \(**Сервис\/Диспетчер фрагментов кода**\).  
  
> [!TIP]
>  Сведения о способах написания фрагментов кода попроще, поищите на веб\-сайте CodePlex средства сообщества, такие как [Редактор фрагментов \(Snippet Editor\)](http://go.microsoft.com/fwlink/?LinkId=251033).  
  
## Шаблон фрагмента  
 Ниже приведен простой шаблон фрагмента:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CodeSnippets  
    xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title></Title>  
        </Header>  
        <Snippet>  
            <Code Language="">  
                <![CDATA[]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
  
```  
  
### Создание фрагмента кода  
  
1.  Создайте новый XML\-файл в Visual Studio и добавьте показанный выше шаблон.  
  
2.  Введите заголовок фрагмента, например "Hello World VB" в элементе заголовка.  
  
3.  Заполните язык фрагмента в атрибуте языка элемента кода.  Для этого примера используйте "VB".  
  
4.  Добавьте какой\-нибудь код в раздел CDATA внутри элемента Code, например:  
  
    ```  
    <Code Language="VB">  
        <![CDATA[Console.WriteLine("Hello, World!")]]>  
    </Code>  
  
    ```  
  
5.  Сохраните фрагмент как VBCodeSnippet.snippet.  
  
### Добавление фрагмента кода в Visual Studio  
  
1.  Можно добавлять свои собственные фрагменты в установку Visual Studio с помощью диспетчера фрагментов кода.  Откройте Диспетчер фрагментов кода \(**Средства\/Диспетчер фрагментов кода**\).  
  
2.  Нажмите кнопку **Импорт**.  
  
3.  Перейдите к папке, в которой сохранен фрагмента кода в предыдущей процедуре, выделите его и нажмите кнопку **Открыть**.  
  
4.  Откроется диалоговое окно **Импорт фрагмента кода**, в котором будет предложено выбрать место добавления фрагмента \(из вариантов в правой панели\).  Один из вариантов должен быть **Мои фрагменты кода**.  Выберите его и нажмите **Готово** и нажмите кнопку **ОК**.  
  
5.  Фрагмент копируется в следующее расположение:  
  
     `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippets`  
  
6.  Протестируйте свой фрагмент, открыв проект Visual Basic и открыв файл кода.  В файле щелкните **Вставить фрагмент** в контекстном меню, затем выберите **Мои фрагменты кода**.  Вы должны увидеть фрагмент с именем **Мой фрагмента кода Visual Basic**.  Дважды щелкните его.  
  
7.  Нужно увидеть `Console.WriteLine("Hello, World!")`, вставленный в код.  
  
### Добавление полей описания и сочетания клавиш  
  
1.  Поля Описания предоставляют дополнительные сведения о вашем фрагменте кода при просмотре в диспетчере фрагментов кода.  Ярлык — это тег, который пользователи могут вводить для вставки фрагмента.  Измените фрагмент, добавленный путем открытия файла `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet`.  
  
2.  Добавьте элементы Автор и Описание в элемент Заголовок, и заполните их.  
  
3.  Элемент Заголовок выглядят примерно следующим образом:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
    </Header>  
  
    ```  
  
4.  Откройте Диспетчер фрагментов кода и выберите фрагмент кода.  В правой области вы увидите, что поля Описание и Автор теперь заполнены.  
  
5.  Чтобы добавить ярлык, добавьте элемент "Ярлык" рядом с элементом "Автор" и "Описание":  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
        <Shortcut>hello</Shortcut>  
    </Header>  
  
    ```  
  
6.  Сохраните файл фрагмента снова.  
  
7.  Чтобы протестировать ярлык, откройте проект Visual Basic и откройте файл кода.  Введите в файле `hello` и нажмите TAB.  Код фрагмента должен быть вставлен.  
  
### Добавление ссылок и импортов  
  
1.  С фрагментами Visual Basic можно добавить ссылку на проект с помощью элемента «Ссылки» и добавить декларацию «Импорты», используя элемент «Импорты». \(Фрагменты в других языках не имеют такой функции\). Например, при изменении `Console.WriteLine` в примере кода на `MessageBox.Show`, может быть нужно добавить сборку System.Windows.Forms.dll в проект.  
  
2.  Откройте фрагмент.  
  
3.  Добавьте элемент "References" в элемент "Фрагмент кода":  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Windows.Forms.dll</Assembly>  
        </Reference>  
    </References>  
  
    ```  
  
4.  Добавьте элемент "импорты" в элемент "Фрагмент кода":  
  
    ```  
    <Imports>  
        <Import>  
           <Namespace>System.Windows.Forms</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
5.  Измените раздел CDATA на следующее:  
  
    ```  
    <![CDATA[MessageBox.Show("Hello, World!")]]>  
    ```  
  
6.  Сохраните фрагмент.  
  
7.  Откройте проект Visual Basic и добавьте фрагмент.  
  
8.  Вы увидите инструкцию импортов в верхней части файла кода.  
  
    ```  
    Imports System.Windows.Forms  
  
    ```  
  
9. Посмотрите на Свойства проекта.  Вкладка "Ссылки" содержит ссылку на System.Windows.Forms.dll.  
  
### Добавление замен  
  
1.  Пользователю может потребоваться заменить части фрагментов кода, например при добавлении переменной, а пользователю необходимо заменить переменную на другую в текущем проекте.  Можно предоставить 2 типа замен: литералы и объекты.  Литералы — строки определенного типа \(строковые литералы, имена переменных, или строковые представления числовых значений\).  Объекты — это экземпляры некоторого типа, кроме строки.  В этой процедуре будет добавлена замена литерала и замена объекта и изменен код для учета этих замен.  
  
2.  Откройте фрагмент.  
  
3.  В этом примере используется строка подключения SQL, поэтому необходимо изменить элементы импортов и ссылок для добавления соответствующих ссылок:  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Data.dll</Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>System.Xml.dll</Assembly>  
        </Reference>  
    </References>  
    <Imports>  
        <Import>  
            <Namespace>System.Data</Namespace>  
        </Import>  
        <Import>  
            <Namespace>System.Data.SqlClient</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
4.  Для объявления литеральной замены для строки подключения SQL добавьте элемент Declarations под элементом Snippet, а в нем добавьте элемент Literal с вложенными элементами для идентификатора, всплывающей подсказки и значения по умолчанию для замены.  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
    </Declarations>  
  
    ```  
  
5.  Чтобы объявить замену объекта для подключения SQL, добавьте элемент Object внутри элемента Declarations и добавьте вложенные элементы для идентификатора, типа объекта, подсказки и значения по умолчанию.  Результирующий элемент Declarations должен выглядеть следующим образом:  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
        <Object>  
            <ID>SqlConnection</ID>  
            <Type>System.Data.SqlClient.SqlConnection</Type>  
            <ToolTip>Replace with a connection object in your application.</ToolTip>  
            <Default>dcConnection</Default>  
        </Object>  
    </Declarations>  
    ```  
  
6.  В разделе кода, можно обращаться к заменам окружающими знаками $, например `$замена$`.  
  
    ```  
    <Code Language="VB" Kind="method body">  
        <![CDATA[Dim daCustomers As SqlDataAdapter  
            Dim selectCommand As SqlCommand  
  
            daCustomers = New SqlClient.SqlDataAdapter()  
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)  
            daCustomers.SelectCommand = selectCommand  
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>  
    </Code>  
    ```  
  
7.  Сохраните фрагмент.  
  
8.  Откройте проект Visual Basic и добавьте фрагмент.  
  
9. Код должен выглядеть следующим образом, где замены `строка подключения SQL` и `dcConnection` выделены светло\-оранжевым цветом.  Для перехода от одного к другому нажмите TAB.  
  
    ```  
    Dim daCustomers As SqlDataAdapter  
    Dim selectCommand As SqlCommand  
  
    daCustomers = New SqlClient.SqlDataAdapter()  
    selectCommand = New SqlClient.SqlCommand("SQL connection string")  
    daCustomers.SelectCommand = selectCommand  
    daCustomers.SelectCommand.Connection = dcConnection  
  
    ```  
  
## См. также  
 [Справочник по схеме фрагментов кода](../ide/code-snippets-schema-reference.md)