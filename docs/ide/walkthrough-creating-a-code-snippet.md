---
title: Пошаговое руководство. Создание фрагмента кода
ms.date: 06/10/2019
ms.topic: conceptual
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6f58581a601da59e7ff66a3bae5ddcb7432bf8e3
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836103"
---
# <a name="walkthrough-create-a-code-snippet"></a>Пошаговое руководство. Создание фрагмента кода

Фрагмент кода можно создать всего в несколько шагов. Все, что необходимо сделать, — это создать XML-файл, заполнить соответствующие элементы и добавить в него код. При необходимости следует использовать параметры замены и ссылками на проект. Импорт фрагмента кода установки Visual Studio с помощью **импорта** кнопку **Диспетчер фрагментов кода** (**средства** > **кода Диспетчер фрагментов**).

## <a name="snippet-template"></a>Шаблон фрагмента

Следующий код XML — это простой шаблон фрагмента:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
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

## <a name="create-a-code-snippet"></a>Создание фрагмента кода

1. Создайте XML-файл в Visual Studio и добавьте показанный выше шаблон.

2. Введите заголовок фрагмента в **Title** элемент. Использовать название **квадратный корень**.

3. Укажите язык фрагмента кода в атрибуте **Language** элемента **Code**. Для C#, использовать **CSharp**и Visual Basic, используйте **VB**.

   > [!TIP]
   > Чтобы увидеть значения всех доступных языков, Обзор [кода раздел атрибутов элемента](code-snippets-schema-reference.md#attributes) на [Справочник по схеме фрагментов кода](code-snippets-schema-reference.md) страницы.

4. Добавьте фрагмент кода в **CDATA** разделе внутри **кода** элемент.

   Для C#:

   ```xml
   <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt(16);]]>
   </Code>
   ```

   Или для Visual Basic:

   ```xml
   <Code Language="VB">
       <![CDATA[Dim root = Math.Sqrt(16)]]>
   </Code>
   ```

5. Сохраните фрагмент как *SquareRoot.snippet* (его можно сохранить в любом месте).

## <a name="import-a-code-snippet"></a>Импорт фрагмента кода

1. Фрагмент кода можно импортировать в папку установки Visual Studio с помощью **Диспетчер фрагментов кода**. Откройте его, выбрав **средства** > **Диспетчер фрагментов кода**.

2. Нажмите кнопку **Импорт**.

3. Перейдите к папке, в которой был сохранен фрагмент кода в предыдущей процедуре, выделите его и нажмите кнопку **Открыть**.

4. Откроется диалоговое окно **Импорт фрагмента кода**, в котором будет предложено выбрать место добавления фрагмента (из вариантов в правой области). Один из вариантов должен быть **Мои фрагменты кода**. Выберите его и нажмите кнопку **Готово**, а затем — кнопку **ОК**.

5. Фрагмент копируется на один из следующих расположений, в зависимости от языка кода:

   ::: moniker range="vs-2017"

   *%USERPROFILE%\Documents\Visual studio 2017\Code Snippets\Visual C#фрагменты кода \My*
    *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My фрагменты кода*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual studio 2019\Code Snippets\Visual C#фрагменты кода \My*
    *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual Basic\My фрагменты кода*

   ::: moniker-end

6. Протестируйте фрагмент, открыв C# проект или Visual Basic. Откройте в редакторе кода файл, выберите **фрагменты** > **вставить фрагмент** из контекстного меню, затем **Мои фрагменты кода**. Вы должны увидеть фрагмент с именем **квадратный корень**. Дважды щелкните его.

   Фрагмент кода вставляется в файле кода.

## <a name="description-and-shortcut-fields"></a>Поля "Описание" и "ярлык

::: moniker range="vs-2017"

1. Поля Description предоставляют дополнительные сведения о вашем фрагменте кода при просмотре в диспетчере фрагментов кода. Ярлык — это тег, который пользователи могут вводить для вставки фрагмента. Измените фрагмент, добавленный путем открытия файла *%USERPROFILE%\Documents\Visual Studio 2017\Code фрагменты\\[Visual C# или Visual Basic] \My Code Snippet\SquareRoot.snippet*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Поля Description предоставляют дополнительные сведения о вашем фрагменте кода при просмотре в диспетчере фрагментов кода. Ярлык — это тег, который пользователи могут вводить для вставки фрагмента. Измените фрагмент, добавленный путем открытия файла *%USERPROFILE%\Documents\Visual Studio 2019\Code фрагменты\\[Visual C# или Visual Basic] \My Code Snippet\SquareRoot.snippet*.

::: moniker-end

   > [!TIP]
   > Так как вы изменяете файл в каталоге, где он помещен в Visual Studio, не нужно заново импортировать ее в Visual Studio.

2. Добавьте элементы **Author** и **Description** в элемент **Header** и заполните их.

3. Элемент **Header** должен выглядеть примерно так:

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. Откройте **диспетчер фрагментов кода** и выберите фрагмент кода. Обратите внимание, что в области справа **описание** и **автор** теперь поля.

   ![Описание фрагмента кода в диспетчере фрагментов кода](media/code-snippet-description-author.png)

5. Чтобы добавить ярлык, добавьте **ярлык** сервисном **заголовок** элемент:

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. Сохраните файл фрагмента еще раз.

7. Чтобы протестировать ярлык, откройте проект, который использовался ранее, введите **sqrt** в редакторе и нажмите клавишу **вкладке** (один раз для Visual Basic дважды для C#).

   Код фрагмента должен быть вставлен.

## <a name="replacement-parameters"></a>Параметры замены

Вы можете части фрагмента кода, заменяемого этим пользователем. Например может потребоваться пользователю замените имя переменной в текущем проекте. Возможны два типа замен: литералы и объекты. Используйте [элемент Literal](code-snippets-schema-reference.md#literal-element) для определения замещающего элемента для фрагмент кода, который полностью заключен во фрагмент кода, но скорее всего будет изменен после вставки в код (например, строковое или числовое значение). Используйте [объектного элемента](code-snippets-schema-reference.md#object-element) для определения элемента, который необходим во фрагменте кода, но скорее всего будет определен вне самого (к примеру, экземпляр объекта или элемента управления) фрагмента.

1. Чтобы пользователи могли легко заменить номер, для которого требуется вычислить квадратный корень, измените **фрагмент** элемент *SquareRoot.snippet* файл следующим образом:

   ```xml
   <Snippet>
     <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt($Number$);]]>
     </Code>
     <Declarations>
       <Literal>
         <ID>Number</ID>
         <ToolTip>Choose the number you want the square root of.</ToolTip>
         <Default>16</Default>
       </Literal>
     </Declarations>
   </Snippet>
   ```

   Обратите внимание на то, что замена литерала, присваивается идентификатор (`Number`). Что идентификатор ссылается из фрагмента кода путем заключения его с `$` символов:

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. Сохраните файл фрагмента.

3. Откройте проект и вставить фрагмент кода.

   Вставить фрагмент кода и редактируемой литерала выделяется для замены. Наведите указатель мыши замещающий параметр, чтобы увидеть подсказку для значения.

   ![Код подсказки параметров замены фрагмент кода в Visual Studio](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > Если имеется более одного параметра replacable во фрагменте, можно нажать **вкладке** для перехода от одного в другой, чтобы изменить значения.

## <a name="import-a-namespace"></a>Импорт пространства имен

Фрагмент кода можно использовать для добавления `using` директива (C#) или `Imports` оператор (Visual Basic), включив [элемент Imports](code-snippets-schema-reference.md#imports-element). Для проектов .NET Framework, можно также добавить ссылку на проект с помощью [элемент References](code-snippets-schema-reference.md#references-element).

Следующий код XML показан фрагмент кода, которая использует метод `File.Exists` в пространстве имен System.IO и, таким образом, определяет **Imports** элемент для импорта пространства имен System.IO.

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>File Exists</Title>
      <Shortcut>exists</Shortcut>
    </Header>
    <Snippet>
      <Code Language="CSharp">
        <![CDATA[var exists = File.Exists("C:\\Temp\\Notes.txt");]]>
      </Code>
      <Imports>
        <Import>
          <Namespace>System.IO</Namespace>
        </Import>
      </Imports>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>См. также

- [Справочник по схеме фрагментов кода](../ide/code-snippets-schema-reference.md)