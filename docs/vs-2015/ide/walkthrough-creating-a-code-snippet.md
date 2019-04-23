---
title: Пошаговое руководство. Создание фрагмента кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ee4e0c6fd686398ae89b5c079d6efc1297a19f5d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60109813"
---
# <a name="walkthrough-creating-a-code-snippet"></a>Пошаговое руководство. Создание фрагмента кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Фрагмент кода можно создать всего в несколько шагов. Все, что необходимо сделать, — это создать XML-файл, заполнить соответствующие элементы и добавить в него код. В код можно также добавить ссылки и параметры замены. Вы можете добавить фрагмент в папку установки Visual Studio с помощью кнопки "Импорт" в диспетчере фрагментов кода (**Сервис/Диспетчер фрагментов кода**).  
  
> [!TIP]
>  Сведения о способах написания фрагментов кода проще, поиск на веб-сайте CodePlex средства сообщества, например [Snippet Editor](http://go.microsoft.com/fwlink/?LinkId=251033).  
  
## <a name="snippet-template"></a>Шаблон фрагмента  
 Ниже приведен простой шаблон фрагмента.  
  
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
  
### <a name="to-create-a-code-snippet"></a>Создание фрагмента кода  
  
1. Создайте XML-файл в Visual Studio и добавьте показанный выше шаблон.  
  
2. Введите заголовок фрагмента, например "Hello World VB", в элементе Title.  
  
3. Укажите язык фрагмента в атрибуте Languages элемента Code. Для этого примера используйте значение "VB".  
  
4. Добавьте какой-нибудь код в раздел CDATA внутри элемента Code, например:  
  
    ```  
    <Code Language="VB">  
        <![CDATA[Console.WriteLine("Hello, World!")]]>  
    </Code>  
  
    ```  
  
5. Сохраните фрагмент как файл VBCodeSnippet.snippet.  
  
### <a name="to-add-a-code-snippet-to-visual-studio"></a>Добавление фрагмента кода в Visual Studio  
  
1. Вы можете добавлять собственные фрагменты в установку Visual Studio с помощью диспетчера фрагментов кода. Откройте диспетчер фрагментов кода (**Сервис/Диспетчер фрагментов кода**).  
  
2. Нажмите кнопку **Импорт**.  
  
3. Перейдите к папке, в которой был сохранен фрагмент кода в предыдущей процедуре, выделите его и нажмите кнопку **Открыть**.  
  
4. Откроется диалоговое окно **Импорт фрагмента кода**, в котором будет предложено выбрать место добавления фрагмента (из вариантов в правой области). Один из вариантов должен быть **Мои фрагменты кода**. Выберите его и нажмите кнопку **Готово**, а затем — кнопку **ОК**.  
  
5. Фрагмент копируется в следующее расположение:  
  
     `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippets`  
  
6. Протестируйте фрагмент, открыв проект Visual Basic и открыв файл кода. В файле щелкните **вставить фрагмент** в контекстном меню, затем **Мои фрагменты кода**. Вы должны увидеть фрагмент с именем **Мой фрагмента кода Visual Basic**. Дважды щелкните его.  
  
7. Вы должны увидеть `Console.WriteLine("Hello, World!")` вставлены в коде.  
  
### <a name="adding-description-and-shortcut-fields"></a>Добавление полей Description и Shortcut  
  
1. Поля Description предоставляют дополнительные сведения о вашем фрагменте кода при просмотре в диспетчере фрагментов кода. Ярлык — это тег, который пользователи могут вводить для вставки фрагмента. Измените фрагмент, добавленный путем открытия файла `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet`.  
  
2. Добавьте элементы Author и Description в элемент Header и заполните их.  
  
3. Элемент Header должен выглядеть примерно так:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
    </Header>  
  
    ```  
  
4. Откройте диспетчер фрагментов кода и выберите фрагмент кода. В правой области вы увидите, что поля Description и Author теперь заполнены.  
  
5. Чтобы добавить ярлык, добавьте элемент Shortcut рядом с элементами Author и Description:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
        <Shortcut>hello</Shortcut>  
    </Header>  
  
    ```  
  
6. Сохраните файл фрагмента еще раз.  
  
7. Чтобы протестировать ярлык, откройте проект Visual Basic и откройте файл кода. Тип `hello` в файле и нажмите клавишу TAB. Должен быть вставлен фрагмент кода.  
  
### <a name="to-add-references-and-imports"></a>Добавление ссылок и объявлений импорта  
  
1. С фрагментами Visual Basic можно добавить ссылку на проект с помощью элемента References и добавьте объявление импорта с помощью элемента Imports. (Фрагменты кода на других языках не имеют эту функцию). Например, при изменении `Console.WriteLine` в примере кода на `MessageBox.Show` может потребоваться добавить сборку System.Windows.Forms.dll в проект.  
  
2. Откройте фрагмент.  
  
3. Добавьте элемент References в элементе Snippet:  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Windows.Forms.dll</Assembly>  
        </Reference>  
    </References>  
  
    ```  
  
4. Добавьте элемент Imports в элементе Snippet:  
  
    ```  
    <Imports>  
        <Import>  
           <Namespace>System.Windows.Forms</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
5. Измените раздел CDATA на следующий:  
  
    ```  
    <![CDATA[MessageBox.Show("Hello, World!")]]>  
    ```  
  
6. Сохраните фрагмент.  
  
7. Откройте проект Visual Basic и добавьте фрагмент.  
  
8. Вы увидите оператор Imports в верхней части файла кода.  
  
    ```  
    Imports System.Windows.Forms  
  
    ```  
  
9. Просмотрите свойства проекта. Вкладка "Ссылки" содержит ссылку на System.Windows.Forms.dll.  
  
### <a name="adding-replacements"></a>Добавление замен  
  
1. Вам может потребоваться обеспечить возможность заменять части фрагмента кода, например, если вы добавляете переменную и хотите, чтобы пользователь заменил ее на другую в текущем проекте. Возможны два типа замен: литералы и объекты. Литералы — это строки определенного типа (строковые литералы, имена переменных или строковые представления числовых значений). Объекты — это экземпляры некоторого типа, кроме строки. В этой процедуре будут объявлены замена литерала и замена объекта и изменен код для учета этих замен.  
  
2. Откройте фрагмент.  
  
3. В этом примере используется строка подключения SQL, поэтому необходимо изменить элементы Imports и References, добавив соответствующие ссылки:  
  
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
  
4. Для объявления литеральной замены для строки подключения SQL добавьте элемент Declarations под элементом Snippet, а в нем добавьте элемент Literal с вложенными элементами для идентификатора, подсказки и значения по умолчанию.  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
    </Declarations>  
  
    ```  
  
5. Чтобы объявить замену объекта для подключения SQL, добавьте элемент Object внутри элемента Declarations и добавьте вложенные элементы для идентификатора, типа объекта, подсказки и значения по умолчанию. В итоге элемент Declarations должен выглядеть следующим образом:  
  
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
  
6. В разделе кода замены обозначаются символами $ в начале и конце, например `$replacement$`.  
  
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
  
7. Сохраните фрагмент.  
  
8. Откройте проект Visual Basic и добавьте фрагмент.  
  
9. Код должен выглядеть так, как показано ниже. Замены `SQL connection string` и `dcConnection` выделены светло-оранжевым цветом. Нажмите клавишу TAB для перехода от одного к другому.  
  
    ```  
    Dim daCustomers As SqlDataAdapter  
    Dim selectCommand As SqlCommand  
  
    daCustomers = New SqlClient.SqlDataAdapter()  
    selectCommand = New SqlClient.SqlCommand("SQL connection string")  
    daCustomers.SelectCommand = selectCommand  
    daCustomers.SelectCommand.Connection = dcConnection  
  
    ```  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме фрагментов кода](../ide/code-snippets-schema-reference.md)
