---
title: Пошаговое руководство. Реализация фрагментов кода | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ae22475fa488d93ac4660fdc0cf567f50b32029
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052120"
---
# <a name="walkthrough-implement-code-snippets"></a>Пошаговое руководство. Реализация фрагментов кода
Можно создавать фрагменты кода и включать их в расширении редактора, чтобы пользователи расширения их можно добавить в свой собственный код.

 Фрагмент кода является фрагментом кода или другой текст, который может быть включен в файл. Чтобы просмотреть все фрагменты кода, которые были зарегистрированы для определенных языков программирования, на **средства** меню, щелкните **Диспетчер фрагментов кода**. Чтобы вставить фрагмент кода в файле, место фрагмента, щелкните правой кнопкой мыши щелкните Вставить фрагмент или **окружить**, найдите фрагмент кода, требуется и дважды щелкните его. Нажмите клавишу **вкладке** или **Shift**+**вкладке** изменять соответствующие части фрагмента кода и нажмите клавишу **ввод** или **Esc** принять их. Дополнительные сведения см. в разделе [фрагменты кода](../ide/code-snippets.md).

 Фрагмент кода содержится в XML-файл имеет расширение имени файла .snippet *. Фрагмент может содержать поля, которые выделены после вставки фрагмента, чтобы пользователь мог найти и изменить их. Файл фрагмента кода также предоставляет сведения о **Диспетчер фрагментов кода** может отображать его имени фрагмента в соответствующей категории. Сведения о схеме фрагмента, см. в разделе [Справочник по схеме фрагментов кода](../ide/code-snippets-schema-reference.md).

 В этом пошаговом руководстве объясняется, как выполнять эти задачи:

1. Создайте и зарегистрируйте фрагменты кода для конкретного языка.

2. Добавить **вставить фрагмент** команды в контекстное меню.

3. Реализуйте расширение фрагмента кода.

   Это пошаговое руководство основано на [Пошаговое руководство: Отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md).

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, не устанавливайте Visual Studio SDK в центре загрузки. Этот пакет включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-and-register-code-snippets"></a>Создание и регистрация фрагменты кода
 Как правило фрагменты кода связаны с зарегистрированного языковой службой. Тем не менее, у вас нет реализации <xref:Microsoft.VisualStudio.Package.LanguageService> регистрируемый фрагменты кода. Вместо этого просто укажите идентификатор GUID в файле фрагмента индекса, а затем использовать тот же самый GUID в <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> , добавьте в проект.

 Следующие шаги демонстрируют, как создавать фрагменты кода и связывать их с конкретный идентификатор GUID.

1. Создайте следующую структуру каталогов:

    **%InstallDir%\TestSnippets\Snippets\1033\\**

    где *% InstallDir %* — папка установки Visual Studio. (Несмотря на то, что этот путь обычно используется для установки фрагментов кода, можно указать любой путь.)

2. Создайте в папке \1033\ *.xml* файл и назовите его **TestSnippets.xml**. (Несмотря на то, что это имя обычно используется для индекса файл фрагмента кода, можно указать любое имя, до тех пор, пока он имеет *.xml* расширение имени файла.) Добавьте следующий текст и удалить местозаполнитель GUID и добавлять свои собственные.

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

3. Создайте файл в папку фрагментов, назовите его **тестирования**`.snippet`, а затем добавьте следующий текст:

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

   Ниже показано, как зарегистрировать фрагменты кода.

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Чтобы зарегистрировать фрагменты кода для определенного идентификатора GUID

1. Откройте **CompletionTest** проекта. Сведения о создании этого проекта, см. в разделе [Пошаговое руководство: Отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md).

2. В проекте добавьте ссылки на следующие сборки:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.TextManager.Interop.8.0

    - microsoft.msxml

3. В проекте, откройте **source.extension.vsixmanifest** файл.

4. Убедитесь, что **активы** вкладка содержит **VsPackage** содержимого типа и что **проекта** присваивается имя проекта.

5. Выберите проект CompletionTest и в окне свойств задайте **создавать файл Pkgdef** для **true**. Сохраните проект.

6. Добавить статический `SnippetUtilities` класс в проект.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. В классе SnippetUtilities, определите GUID и присвойте ему значение, выбранное на *SnippetsIndex.xml* файла.

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. Добавить <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> для `TestCompletionHandler` класса. Этот атрибут можно добавить для любого общедоступного или внутреннего класса (не статического) в проекте. (Может потребоваться добавить `using` оператор для пространства имен Microsoft.VisualStudio.Shell.)

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Постройте и запустите проект. Фрагмент кода, зарегистрированным в экспериментальном экземпляре Visual Studio, которая запускается при выполнении проекта, должно отображаться в **Диспетчер фрагментов кода** под **TestSnippets** языка.

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Добавьте команду Вставить фрагмент в контекстное меню
 **Вставить фрагмент** команды, не включенные в контекстном меню текстового файла. Таким образом необходимо включить команды.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Чтобы добавить команду Вставить фрагмент в контекстное меню

1. Откройте `TestCompletionCommandHandler` файл класса.

     Поскольку этот класс реализует <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, вы можете активировать **вставить фрагмент** в команду <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод. Прежде чем включить команду, проверьте, что этот метод не вызывается внутри функции автоматизации так как при **вставить фрагмент** выборе команды, он отображает пользовательский интерфейс (UI) средство выбора фрагмента.

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. Постройте и запустите проект. В экспериментальном экземпляре откройте файл, содержащий *.zzz* расширение имени файла и затем щелкните правой кнопкой мыши в нем. **Вставить фрагмент** команда должна отображаться в контекстном меню.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Реализуйте расширение фрагмента кода в пользовательском Интерфейсе средства выбора фрагмента
 В этом разделе показано, как реализовать расширение фрагмента кода, таким образом, чтобы средство выбора фрагментов пользовательского интерфейса, которые отображаются после **вставить фрагмент** нажатии в контекстном меню. Фрагмент кода также расширяется, когда пользователь вводит ярлык фрагмента кода и затем нажимает клавишу **вкладке**.

 Чтобы отобразить средство выбора фрагментов пользовательского интерфейса и включение навигации и приемки после вставки фрагмента, используйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод. Сама вставка обрабатывается <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> метод.

 В реализации расширения фрагмента кода используется для прежних версий <xref:Microsoft.VisualStudio.TextManager.Interop> интерфейсов. При переводе классов на текущий момент редактор для устаревшего кода, помните, что устаревшие интерфейсы используют сочетание номеров строк и номера столбцов для указания расположения в текстовом буфере, но текущий классы используют один индекс. Таким образом Если буфер имеет три строки, каждая из которых имеет 10 символов (плюс новой строки, которая подсчитывает как один символ), четвертый символ в третьей строке находится в позиции 27 в текущей реализации, но он находится в строке 2, позиции 3 в старой реализации.

#### <a name="to-implement-snippet-expansion"></a>Чтобы реализовать расширение фрагмента кода

1. Для файла, содержащего `TestCompletionCommandHandler` класса, добавьте следующий `using` инструкций.

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. Сделать `TestCompletionCommandHandler` Реализуйте класс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> интерфейс.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. В `TestCompletionCommandHandlerProvider` класса, импортируйте <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. Добавьте несколько закрытых полей для интерфейсов расширения кода и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. В конструкторе класса `TestCompletionCommandHandler` класса, заполните следующие поля.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. Чтобы отобразить средство выбора фрагмента, когда пользователь щелкает **вставить фрагмент** команды, добавьте следующий код, чтобы <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод. (Чтобы сделать более удобочитаемым, в этом разделе `Exec()`не показан код, который используется для завершения операторов; вместо этого блоки кода добавляются к существующему методу.) Добавьте следующий блок кода после кода, который проверяет наличие символа.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. Если фрагмент кода содержит поля, можно переходить, сеанс расширения сохраняется открытым, пока не будет явно принимается расширения; Если фрагмент не содержит полей, сеанс закрывается и возвращается в виде `null` по <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> метод. В <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метода, после выбора фрагментов кода пользовательского интерфейса, добавленного на предыдущем шаге, добавьте следующий код для обработки переходов фрагмента (когда пользователь нажимает **вкладке** или **Shift** + **Вкладке** после вставки фрагмента).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. Чтобы вставить фрагмент кода, когда пользователь вводит соответствующий ярлык и затем нажимает клавишу **вкладке**, добавьте код для <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод. Закрытый метод, который вставляет фрагмент будет отображаться на более позднем этапе. Добавьте следующий код после перемещения кода, добавленного на предыдущем шаге.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Реализовать методы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> интерфейс. В данном случае являются только методы интерес <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Другие методы должен просто возвращать <xref:Microsoft.VisualStudio.VSConstants.S_OK>.

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Выполните метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Вспомогательный метод, который фактически вставляет расширения по рассматривается в более позднем этапе. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Сведения строки и столбца, который можно получить из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. Следующий частный метод вставляет фрагмент кода, либо на основе ярлык или имя и путь. Затем он вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> метод фрагментом.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Сборка и тестирование расширения фрагмента кода
 Вы можете протестировать работает расширение фрагмента кода в проекте.

1. Постройте решение. При запуске этого проекта в отладчике, запускается второй экземпляр Visual Studio.

2. Откройте текстовый файл и введите любой текст.

3. Щелкните правой кнопкой мыши где-нибудь в тексте и нажмите кнопку **вставить фрагмент**.

4. Средство выбора фрагментов, пользовательский Интерфейс будет выглядеть с всплывающее окно, говорящее **замены поля тестов**. Дважды щелкните всплывающее окно.

     Следующий фрагмент кода должен быть вставлен.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     Не нажимайте **ввод** или **Esc**.

5. Нажмите клавишу **вкладке** и **Shift**+**вкладке** для переключения между «первый» и «секунду».

6. Принимать вставки, можно нажать клавишу **ввод** или **Esc**.

7. В другой части текста, введите «test» и нажмите клавишу **вкладке**. Так как «test» ярлык фрагмента кода, следует снова вставить фрагмент кода.

## <a name="next-steps"></a>Следующие шаги