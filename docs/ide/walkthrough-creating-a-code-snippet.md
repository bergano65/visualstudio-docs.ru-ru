---
title: Пошаговое руководство. Создание фрагмента кода
description: 'Узнайте, как создать фрагмент кода за три шага: создание XML-файла, заполнение соответствующих элементов и добавление в него кода.'
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: how-to
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 39565b95b93e489a739c2da3a0f88fb9f683a2bc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873805"
---
# <a name="walkthrough-create-a-code-snippet"></a>Пошаговое руководство. Создание фрагмента кода

Фрагмент кода можно создать всего в несколько шагов. Все, что необходимо сделать, — это создать XML-файл, заполнить соответствующие элементы и добавить в него код. При необходимости вы можете использовать параметры замены и ссылки на проект. Импортируйте фрагмент в папку установки Visual Studio с помощью кнопки **Импорт** в **диспетчере фрагментов кода** (**Сервис** > **Диспетчер фрагментов кода**).

## <a name="snippet-template"></a>Шаблон фрагмента

Ниже приведен XML-код простого шаблона фрагмента:

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

2. Введите заголовок фрагмента в элементе **Заголовок**. Используйте заголовок **Square Root** (Квадратный корень).

3. Укажите язык фрагмента кода в атрибуте **Language** элемента **Code**. Для C# используйте **C#** , для Visual Basic — **VB**, а для C++ — **CPP**.

   > [!TIP]
   > Чтобы просмотреть все доступные значения языка, просмотрите раздел об [атрибутах элементов кода](code-snippets-schema-reference.md#attributes) на странице [Справочник по схеме фрагментов кода](code-snippets-schema-reference.md).

4. Добавьте код фрагмента в раздел **CDATA** внутри элемента **Code**.

   Для C#:

   ```xml
   <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt(16);]]>
   </Code>
   ```

   Либо для Visual Basic:

   ```xml
   <Code Language="VB">
       <![CDATA[Dim root = Math.Sqrt(16)]]>
   </Code>
   ```

   > [!NOTE]
   > Для строк кода в разделе **CDATA** фрагмента кода нельзя указать отступы или форматирование. Языковая служба автоматически форматирует вставленный код.

5. Сохраните фрагмент как *SquareRoot.snippet* (его можно сохранить в любом месте).

## <a name="import-a-code-snippet"></a>Импорт фрагмента кода

1. Вы можете импортировать фрагмент в установку Visual Studio с помощью **диспетчера фрагментов кода**. Чтобы открыть его, выберите **Сервис** > **Диспетчер фрагментов кода**.

2. Нажмите кнопку **Импорт**.

3. Перейдите к папке, в которой был сохранен фрагмент кода в предыдущей процедуре, выделите его и нажмите кнопку **Открыть**.

4. Откроется диалоговое окно **Импорт фрагмента кода**, в котором будет предложено выбрать место добавления фрагмента (из вариантов в правой области). Один из вариантов должен быть **Мои фрагменты кода**. Выберите его и нажмите кнопку **Готово**, а затем — кнопку **ОК**.

5. В зависимости от языка кода фрагмент копируется в одно из следующих расположений:

   ::: moniker range="vs-2017"

   *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual C#\My Code Snippets*  
   *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual C#\My Code Snippets*  
   *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

6. Протестируйте фрагмент, открыв проект C# или Visual Basic. Открыв файл кода в редакторе, выберите пункты **Фрагменты** > **Вставить фрагмент** в контекстном меню, а затем щелкните **Мои фрагменты кода**. Вы должны увидеть фрагмент с именем **Square Root**. Дважды щелкните его.

   Код фрагмента вставляется в файл кода.

## <a name="description-and-shortcut-fields"></a>Поля Description и ярлыков

::: moniker range="vs-2017"

1. Поля Description предоставляют дополнительные сведения о вашем фрагменте кода при просмотре в диспетчере фрагментов кода. Ярлык — это тег, который пользователи могут вводить для вставки фрагмента. Измените добавленный фрагмент, открыв файл *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\\[Visual C# или Visual Basic]\My Code Snippet\SquareRoot.snippet*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Поля Description предоставляют дополнительные сведения о вашем фрагменте кода при просмотре в диспетчере фрагментов кода. Ярлык — это тег, который пользователи могут вводить для вставки фрагмента. Измените добавленный фрагмент, открыв файл *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\\[Visual C# или Visual Basic]\My Code Snippet\SquareRoot.snippet*.

::: moniker-end

   > [!TIP]
   > Так как вы изменяете файл в том каталоге, куда его поместила система Visual Studio, вам не нужно заново импортировать его в Visual Studio.

2. Добавьте элементы **Author** и **Description** в элемент **Header** и заполните их.

3. Элемент **Header** должен выглядеть примерно так:

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. Откройте **диспетчер фрагментов кода** и выберите фрагмент кода. В правой области обратите внимание на то, что поля **Description** и **Author** теперь заполнены.

   ![Описание фрагмента кода в диспетчере фрагментов кода](media/code-snippet-description-author.png)

5. Чтобы добавить ярлык, добавьте элемент **Shortcut** внутрь элемента **Header**:

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. Сохраните файл фрагмента еще раз.

7. Чтобы протестировать ярлык, откройте использованный ранее проект, введите **sqrt** в редакторе и нажмите клавишу **TAB** (один раз для Visual Basic или два раза для C#).

   Код фрагмента должен быть вставлен.

## <a name="replacement-parameters"></a>Параметры замены

Возможно, вам нужно предоставить пользователю возможность заменять части фрагмента кода. Например, может потребоваться, чтобы пользователь заменил имя переменной на используемое в текущем проекте. Возможны два типа замен: литералы и объекты. [Элемент Literal](code-snippets-schema-reference.md#literal-element) используется для определения замещающего элемента для отрывка кода, который полностью заключен во фрагмент, но, скорее всего, будет изменен после вставки в код (например, строка или числовое значение). [Элемент Object](code-snippets-schema-reference.md#object-element) используется для определения элемента, который необходим во фрагменте кода, но, скорее всего, будет определен вне самого фрагмента (например, экземпляр объекта или элемент управления).

1. Чтобы пользователь мог легко заменить число, квадратный корень которого требуется вычислить, измените элемент **Snippet** в файле *SquareRoot.snippet* следующим образом:

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

   Обратите внимание, что замещающему литералу назначен идентификатор (`Number`). На этот идентификатор указывает ссылка в фрагменте кода путем заключения его в символы `$`:

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. Сохраните файл фрагмента.

3. Откройте проект и вставьте фрагмент.

   После вставки фрагмента кода редактируемый литерал выделяется для замены. Наведите указатель мыши на замещающий параметр, чтобы увидеть подсказку для значения.

   ![Подсказка для параметра замены фрагмента кода в Visual Studio](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > Если в фрагменте имеется несколько заменяемых параметров, можно нажать клавишу **TAB**, чтобы переходить от одного к другому для изменения значений.

## <a name="import-a-namespace"></a>Импорт пространства имен

Фрагмент кода можно использовать для добавления директивы `using` (C#) или оператора `Imports` (Visual Basic), включив [элемент Imports](code-snippets-schema-reference.md#imports-element). Для проектов .NET Framework вы можете добавить ссылку на проект с помощью [элемента References](code-snippets-schema-reference.md#references-element).

Ниже приведен фрагмент XML-кода, который использует метод `File.Exists` в пространстве имен System.IO и, таким образом, определяет элемент **Imports** для импорта пространства имен System.IO.

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
