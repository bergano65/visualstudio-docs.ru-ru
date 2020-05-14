---
title: 'Пошаговое прохождение: Реализация фрагментов кода Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: ba1b6e0852c1ec1b306938b791eed78e79d211ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697100"
---
# <a name="walkthrough-implement-code-snippets"></a>Прохождение: Реализация фрагментов кода
Можно создавать фрагменты кода и включать их в расширение редактора, чтобы пользователи расширения могли добавлять их в свой собственный код.

 Фрагмент кода — это фрагмент кода или другого текста, который может быть включен в файл. Чтобы просмотреть все фрагменты, зарегистрированные для определенных языков программирования, в меню **Tools** нажмите **Code Snippet Manager.** Чтобы вставить фрагмент в файл, справа щелкните, где вы хотите фрагмент, нажмите Вставьте фрагмент, или **окружить,** найти фрагмент вы хотите, а затем дважды нажмите его. Нажмите **Tab** или **Shift**+**Tab,** чтобы изменить соответствующие части фрагмента, а затем нажмите **Enter** или **Esc,** чтобы принять его. Для получения дополнительной информации смотрите [фрагменты кода](../ide/code-snippets.md).

 Фрагмент кода содержится в файле XML с расширением имени файла .snippet. Фрагмент может содержать поля, которые выделены после вставки фрагмента, чтобы пользователь мог найти и изменить их. Фрагмент файла также предоставляет информацию для **менеджера фрагмента кода,** так что он может отображать имя фрагмента в правильной категории. Для получения информации о схеме [Code snippets schema reference](../ide/code-snippets-schema-reference.md)фрагмента см.

 Это пошаговое промывое учит, как выполнить эти задачи:

1. Создавайте и регистрируйте фрагменты кода для определенного языка.

2. Добавьте команду **Вставки Фрагмент** в меню ярлыка.

3. Реализация расширения фрагмента.

   Это пошаговое походе основано на [завершении работы по выписке по Throughthrough: Display.](../extensibility/walkthrough-displaying-statement-completion.md)

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-and-register-code-snippets"></a>Создание и регистрация фрагментов кода
 Как правило, фрагменты кода связаны с зарегистрированной языковой службой. Тем не менее, вам <xref:Microsoft.VisualStudio.Package.LanguageService> не нужно реализовывать фрагменты кода для регистрации. Вместо этого просто укажите GUID в файле индекса фрагмента, <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> а затем используйте тот же GUID в том, что вы добавляете в свой проект.

 Следующие шаги демонстрируют, как создавать фрагменты кода и связывать их с определенным GUID.

1. Создайте следующую структуру каталога:

    **%InstallDir%-TestSnippets-Snippets-1033\\**

    где *%InstallDir%* является папкой установки Visual Studio. (Хотя этот путь обычно используется для установки фрагментов кода, можно указать любой путь.)

2. В папке «1033» создайте файл *.xml* и назовите его **TestSnippets.xml.** (Хотя это имя обычно используется для файла индекса фрагмента, можно указать любое имя, пока оно имеет расширение имени *файла .xml.)* Добавьте следующий текст, а затем удалите заполнитель GUID и добавьте свой собственный.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <SnippetCollection>
       <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">
           <SnippetDir>
               <OnOff>On</OnOff>
               <Installed>true</Installed>
               <Locale>1033</Locale>
               <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>
               <LocalizedName>Snippets</LocalizedName>
           </SnippetDir>
       </Language>
   </SnippetCollection>
   ```

3. Создайте файл в папке фрагмента, назовите его **тестом,**`.snippet`а затем добавьте следующий текст:

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
       <CodeSnippet Format="1.0.0">
           <Header>
               <Title>Test replacement fields</Title>
               <Shortcut>test</Shortcut>
               <Description>Code snippet for testing replacement fields</Description>
               <Author>MSIT</Author>
               <SnippetTypes>
                   <SnippetType>Expansion</SnippetType>
               </SnippetTypes>
           </Header>
           <Snippet>
               <Declarations>
                   <Literal>
                     <ID>param1</ID>
                       <ToolTip>First field</ToolTip>
                       <Default>first</Default>
                   </Literal>
                   <Literal>
                       <ID>param2</ID>
                       <ToolTip>Second field</ToolTip>
                       <Default>second</Default>
                   </Literal>
               </Declarations>
               <References>
                  <Reference>
                      <Assembly>System.Windows.Forms.dll</Assembly>
                  </Reference>
               </References>
               <Code Language="TestSnippets">
                   <![CDATA[MessageBox.Show("$param1$");
        MessageBox.Show("$param2$");]]>
               </Code>
           </Snippet>
       </CodeSnippet>
   </CodeSnippets>
   ```

   Следующие шаги показывают, как зарегистрировать фрагменты кода.

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Регистрация фрагментов кода для определенного GUID

1. Откройте проект **CompletionTest.** Для получения информации о том, как создать этот проект, [см.](../extensibility/walkthrough-displaying-statement-completion.md)

2. В проекте добавьте ссылки на следующие сборки:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.TextManager.Interop.8.0

    - microsoft.msxml

3. В проекте откройте **файл source.extension.vsixmanifest.**

4. Убедитесь, что вкладка **«Активы»** содержит тип **содержимого VsPackage** и что **проект** настроен на название проекта.

5. Выберите проект CompletionTest и в наборе окон **true**Свойств **Generate Pkgdef File.** Сохраните проект.

6. Добавьте `SnippetUtilities` в проект статический класс.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. В классе SnippetUtilities определите GUID и придайте ему значение, которое вы использовали в файле *SnippetsIndex.xml.*

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. Добавьте <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> в `TestCompletionHandler` класс. Этот атрибут может быть добавлен к любому общедоступному или внутреннему (нестатическому) классу в проекте. (Возможно, вам придется добавить директиву `using` для пространства имен Microsoft.VisualStudio.Shell.)

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Постройте и запустите проект. В экспериментальном экземпляре Visual Studio, который начинается при запуске проекта, фрагмент, который вы только что зарегистрировали, должен отображаться в **коде Snippets Manager** на языке **TestSnippets.**

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Добавьте команду Вставки Фрагмент в меню ярлыка
 Команда **Insert Snippet** не включена в меню ярлыка для текстового файла. Таким образом, вы должны включить команду.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Добавление команды Вставки Фрагмент в меню ярлыка

1. Откройте `TestCompletionCommandHandler` файл класса.

     Поскольку этот <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>класс реализуется, можно активировать команду <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> **Вставки Фрагмент** в методе. Прежде чем включить команду, проверьте, что этот метод не вызывается внутри функции автоматизации, потому что при нажатии команды **Insert Snippet** отображается пользовательский интерфейс насеителя фрагмента (UI).

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. Постройте и запустите проект. В экспериментальном экземпляре откройте файл с расширением имени файла *.zzz,* а затем нажмите вправо в любом месте. Команда **Вставки Фрагмент** должна отображаться в меню ярлыка.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Реализация фрагмента расширения в Snippet Picker UI
 В этом разделе показано, как реализовать расширение фрагмента кода, чтобы uI-образник нащищателя фрагмента отображался при нажатии **на** меню ярлыка. Фрагмент кода также расширяется, когда пользователь вводит ярлык фрагмента кода, а затем нажимает **Tab.**

 Для отображения uI сборщика фрагментов и для обеспечения навигации <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> и приема фрагментов после вставки и приема фрагментов, используйте метод. Сама вставка обрабатывается <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> методом.

 В реализации расширения фрагмента <xref:Microsoft.VisualStudio.TextManager.Interop> кода используются устаревшие интерфейсы. При переводе с текущих классов редактора на устаревший код помните, что устаревшие интерфейсы используют комбинацию строк и номеров столбцов для определения местоположений в буфере текста, но текущие классы используют один индекс. Таким образом, если буфер имеет три строки, каждая из которых имеет 10 символов (плюс новая строка, которая считается одним символом), четвертый символ на третьей строке находится на позиции 27 в текущей реализации, но он находится на строке 2, позиция 3 в старой реализации.

#### <a name="to-implement-snippet-expansion"></a>Для реализации расширения фрагмента

1. В файл, содержащий `TestCompletionCommandHandler` класс, добавьте следующие `using` директивы.

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. Сделайте `TestCompletionCommandHandler` класс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> реализацией интерфейса.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. В `TestCompletionCommandHandlerProvider` классе импортируйте <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. Добавьте несколько частных полей <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>для интерфейсов расширения кода и .

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. В конструкторе класса `TestCompletionCommandHandler` установите следующие поля.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. Чтобы отобразить сборщик фрагментов, когда пользователь нажимает на команду <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> **Insert Snippet,** добавьте следующий код к методу. (Чтобы сделать это объяснение `Exec()`более читаемым, код, используемый для завершения оператора, не отображается; вместо этого блоки кода добавляются к существующему методу.) Добавьте следующий блок кода после кода, который проверяет на наличие символа.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. Если фрагмент имеет поля, которые можно перемещать, сеанс расширения остается открытым до тех пор, пока расширение не будет явно принято; если фрагмент не имеет полей, `null` <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> сеанс закрывается и возвращается как метод. В <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> методе, после кода ui snippet picker, который вы добавили на предыдущем этапе, добавьте следующий код для обработки навигации фрагмента (когда пользователь нажимает **Tab** или **Shift**+**Tab** после вставки фрагмента).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. Чтобы вставить фрагмент кода, когда пользователь вводит соответствующий ярлык, а затем <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> нажимает **Tab,** добавьте код к методу. Частный метод, вставляемый фрагмент, будет показан на более позднем этапе. Добавьте следующий код после навигационного кода, который вы добавили на предыдущем этапе.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Реализация методов интерфейса. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> В этой реализации, только методы интереса <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Другие методы должны <xref:Microsoft.VisualStudio.VSConstants.S_OK>просто вернуться .

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Выполните метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Метод помощника, который фактически вставляет расширения, покрыт более поздним шагом. Предоставляет <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> информацию о строке и столбце, которую <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>вы можете получить от .

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. Следующий частный метод вставляет фрагмент кода, основанный либо на ярлыке, либо на заголовке и пути. Затем <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> он вызывает метод со фрагментом.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Расширение фрагмента кода сборки и тестирования
 Вы можете проверить, работает ли расширение фрагмента в вашем проекте.

1. Создайте решение. При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

2. Откройте текстовый файл и введите текст.

3. Правый щелчок где-то в тексте, а затем нажмите **Вставить фрагмент**.

4. Фрагмент сборщика uI должен отображаться с всплывающими, что говорит **тест замены полей.** Дважды щелкните всплывающее окно.

     Следующий фрагмент должен быть вставлен.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     Не нажимаете **Enter** или **Esc.**

5. Нажмите **Tab** и **Shift**+**Tab,** чтобы переключаться между "первым" и "вторым".

6. Примите вставку, нажав либо **Enter** или **Esc**.

7. В другой части текста введите "тест", а затем нажмите **Tab**. Поскольку "тест" является ярлыком для фрагмента кода, фрагмент должен быть вставлен снова.

## <a name="next-steps"></a>Следующие шаги
