---
title: "Пошаговое руководство: Реализация фрагменты кода | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 17
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Пошаговое руководство: Реализация фрагменты кода
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно создавать фрагменты кода и включать их в расширение редактора, чтобы пользователи расширения их можно добавить собственный код.  
  
 Фрагмент кода является фрагментом кода или другой текст, который может быть включен в файл. Чтобы просмотреть все фрагменты, которые были зарегистрированы для отдельных языков программирования на **средства** меню, щелкните **Code Snippet Manager**. Чтобы вставить фрагмент кода в файле место фрагмента, щелкните правой кнопкой мыши щелкните **Вставить фрагмент** или **Окружить**, фрагмент, который требуется найти и дважды щелкните его. Нажмите клавишу TAB или SHIFT \+ TAB для изменения значимые части фрагмента и нажмите клавишу ВВОД или ESC, чтобы принять его. Дополнительные сведения см. в разделе [Фрагменты кода](../ide/code-snippets.md).  
  
 Фрагмент кода содержится в XML\-файл с расширением .snippet. Фрагмент может содержать поля, которые выделены после вставки фрагмента кода, чтобы пользователь мог найти и изменить их. Файл фрагмента кода также предоставляет сведения о **Code Snippet Manager** чтобы он мог выводить имени фрагмента в соответствующей категории. Сведения о схеме фрагмента в разделе [Справочник по схеме фрагментов кода](../ide/code-snippets-schema-reference.md).  
  
 В этом пошаговом руководстве объясняется, как выполнять эти задачи:  
  
1.  Создайте и зарегистрируйте фрагменты кода для конкретного языка.  
  
2.  Добавить **Вставить фрагмент** команду в контекстном меню.  
  
3.  Реализация расширения фрагмент.  
  
 Это пошаговое руководство основано на [Пошаговое руководство: Отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## Обязательные компоненты  
 Для выполнения данного пошагового руководства, необходимо установить пакет SDK для Visual Studio. Для получения дополнительной информации см. [SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Создание и регистрация фрагменты кода  
 Как правило фрагменты кода связаны с зарегистрированными языковой службы. Тем не менее, вам не нужно реализовать <xref:Microsoft.VisualStudio.Package.LanguageService> для регистрации фрагменты кода. Вместо этого просто укажите идентификатор GUID в файле индекса фрагмента кода и затем использовать идентификатор GUID в <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> добавьте в проект.  
  
 Следующие шаги демонстрируют, как создавать фрагменты кода и связать их с конкретный идентификатор GUID.  
  
1.  Создайте следующую структуру каталогов:  
  
     **%INSTALLDIR%\\TestSnippets\\Snippets\\1033\\**  
  
     где *% InstallDir %* — папка установки Visual Studio. \(Хотя этот путь обычно используется, чтобы установить фрагменты кода, можно указать любой путь.\)  
  
2.  В папке \\1033\\ создайте XML\-файл и назовите его **TestSnippets.xml**. \(Несмотря на то, что это имя обычно используется для индекса файла фрагмента кода, можно указать любое имя, пока он имеет расширение .xml.\) Добавьте следующий текст и удалить местозаполнитель GUID и добавлять свои собственные.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?> <SnippetCollection> <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}"> <SnippetDir> <OnOff>On</OnOff> <Installed>true</Installed> <Locale>1033</Locale> <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath> <LocalizedName>Snippets</LocalizedName> </SnippetDir> </Language> </SnippetCollection>  
    ```  
  
3.  Создайте файл в папку фрагментов, назовите его **тестирования**`.snippet`, а затем добавьте следующий текст:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?> <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet"> <CodeSnippet Format="1.0.0"> <Header> <Title>Test replacement fields</Title> <Shortcut>test</Shortcut> <Description>Code snippet for testing replacement fields</Description> <Author>MSIT</Author> <SnippetTypes> <SnippetType>Expansion</SnippetType> </SnippetTypes> </Header> <Snippet> <Declarations> <Literal> <ID>param1</ID> <ToolTip>First field</ToolTip> <Default>first</Default> </Literal> <Literal> <ID>param2</ID> <ToolTip>Second field</ToolTip> <Default>second</Default> </Literal> </Declarations> <References> <Reference> <Assembly>System.Windows.Forms.dll</Assembly> </Reference> </References> <Code Language="TestSnippets"> <![CDATA[MessageBox.Show("$param1$"); MessageBox.Show("$param2$");]]> </Code> </Snippet> </CodeSnippet> </CodeSnippets>  
    ```  
  
 Ниже показано, как зарегистрировать фрагменты кода.  
  
#### Чтобы зарегистрировать фрагменты кода для определенного идентификатора GUID  
  
1.  Откройте **CompletionTest** проекта. Дополнительные сведения о создании этого проекта в разделе [Пошаговое руководство: Отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2.  В проекте добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   Microsoft.MSXML  
  
3.  В проекте откройте файл source.extension.vsixmanifest.  
  
4.  Убедитесь, что **активы** вкладка содержит **VsPackage** содержимого типа и что **проекта** присваивается имя проекта.  
  
5.  Выберите проект CompletionTest и в окне «Свойства» задайте **создавать файл Pkgdef** для **true**. Сохраните проект.  
  
6.  Добавление статического `SnippetUtilities` класс в проект.  
  
     [!code-cs[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  В классе SnippetUtilities определить GUID и присвойте ему значение, используемое в файле SnippetsIndex.xml.  
  
     [!code-cs[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  Добавить <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> к `TestCompletionHandler` класса. Этот атрибут можно добавить к любому классу \(не статического\) public или internal в проекте. \(Может потребоваться добавить `using` оператор для пространства имен Microsoft.VisualStudio.Shell.\)  
  
     [!code-cs[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. Постройте и запустите проект. В экспериментальном экземпляре Visual Studio, которая запускается при выполнении проекта фрагмент, только что зарегистрированных должно отображаться в **Диспетчер фрагментов кода** под **TestSnippets** языка.  
  
## Добавление команды вставки фрагмента в контекстном меню  
 **Вставить фрагмент** команда не входит в контекстное меню для текстового файла. Таким образом необходимо включить команды.  
  
#### Добавление в контекстном меню команду Вставить фрагмент кода  
  
1.  Откройте `TestCompletionCommandHandler` файл класса.  
  
     Поскольку этот класс реализует <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, вы можете активировать **Вставить фрагмент** в <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод. Прежде чем включить команду, проверьте, что этот метод не вызывается внутри функции автоматизации так как при **Вставить фрагмент** выборе команды, он будет отображать пользовательский интерфейс \(UI\) средство выбора фрагмента.  
  
     [!code-cs[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  Постройте и запустите проект. В экспериментальном экземпляре откройте файл с расширением имени файла .zzz и щелкните правой кнопкой мыши в любом месте в ней.**Вставить фрагмент** команда должна появиться в контекстном меню.  
  
## Реализация расширения фрагмент в средстве выбора фрагмента пользовательского интерфейса  
 В этом разделе показано, как реализовать расширение фрагмент кода таким образом, выбора фрагментов кода пользовательского интерфейса отображается, когда **Вставить фрагмент** нажатии в контекстном меню. Фрагмент кода также расширяется, когда пользователь вводит ярлык фрагмента кода и затем нажимает клавишу TAB.  
  
 Для отображения пользовательского интерфейса выбора фрагментов кода и включение навигации и приемки после вставки фрагмента, используйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод. Сама вставка обрабатывается <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> метод.  
  
 Реализация расширения фрагмент кода использует прежних версий <xref:Microsoft.VisualStudio.TextManager.Interop> интерфейсов. При переводе текущий редактор классов для устаревшего кода, помните, что устаревшие интерфейсы использовать сочетание номера строки и номера столбца для указания местоположения в текстовом буфере, но текущий классы используют один индекс. Таким образом Если буфер имеет три строки, каждая из которых имеет десяти символов \(плюс новой строки, которая считается 1 символ\), четвертый символ в третьей строке находится в позиции 27 в текущей реализации, но это в строке 2, позиции 3 в старой реализации.  
  
#### Для реализации расширения фрагмент  
  
1.  Файл, который содержит `TestCompletionCommandHandler` Добавьте следующие `using` инструкции.  
  
     [!code-cs[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  Сделать `TestCompletionCommandHandler` реализовать класс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> интерфейса.  
  
     [!code-cs[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  В `TestCompletionCommandHandlerProvider` класса, импортируйте <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.  
  
     [!code-cs[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  Добавьте закрытый поля для интерфейсов расширения кода и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-cs[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  В конструкторе `TestCompletionCommandHandler` класса, задайте следующие поля.  
  
     [!code-cs[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  Для отображения выбора фрагментов кода, когда пользователь щелкает **Вставить фрагмент** команды, добавьте следующий код в <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод. \(Чтобы сделать это объяснение более понятным, не содержится Exec\(\) код, который используется для выполнения инструкции; вместо этого блоки кода добавляются к существующему методу\). Добавьте следующий блок кода после кода, который проверяет наличие символа.  
  
     [!code-cs[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  Если фрагмент есть поля, которые можно просматривать, расширения сеанса остается открытой, пока не будет явно принимается расширения; Если фрагмент не содержит полей, сеанс закрывается и возвращается в виде `null`<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> метод. В <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод, после выбора фрагмента кода пользовательского интерфейса, добавленного на предыдущем шаге, добавьте следующий код для обработки переходов фрагмента \(при нажатии клавиши TAB или SHIFT \+ TAB после вставки фрагмента\).  
  
     [!code-cs[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  Чтобы вставить фрагмент кода, когда пользователь вводит соответствующий ярлык и затем нажимает клавишу TAB, добавьте код в <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод. Закрытый метод, который вставляет фрагмент будет отображаться в дальнейшем. Добавьте следующий код после кода навигации, добавленного на предыдущем шаге.  
  
     [!code-cs[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. Реализуйте методы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> интерфейса. В этой реализации только методы, представляющие интерес, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Другие методы просто вернет <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
     [!code-cs[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. Выполните метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Вспомогательный метод, который фактически вставляет расширения будут рассмотрены позже.<xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Информация строки и столбца, который можно получить из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-cs[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. Следующий частный метод вставляет фрагмент кода, либо на основе ярлык или заголовок и пути. Затем он вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> метод с фрагментом.  
  
     [!code-cs[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## Построение и тестирование расширения фрагмента кода  
 Вы можете протестировать расширения фрагмент кода работает в проекте.  
  
1.  Постройте решение. При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
2.  Откройте текстовый файл и введите текст.  
  
3.  Щелкните правой кнопкой мыши где\-нибудь в тексте, а затем нажмите кнопку **Вставить фрагмент**.  
  
4.  Выбор фрагмента, пользовательский Интерфейс будет выглядеть с всплывающее окно с сообщением **замены поля тестов**. Дважды щелкните всплывающее окно.  
  
     Следующий фрагмент кода следует вставить.  
  
    ```  
    MessageBox.Show("first"); MessageBox.Show("second");  
    ```  
  
     Не нажимайте клавишу ВВОД или ESC.  
  
5.  Нажмите клавишу TAB и SHIFT \+ TAB для переключения между «первый» и «секунду».  
  
6.  Примите вставку нажатием клавиши ВВОД или ESC.  
  
7.  В другой части текста введите «test» и нажмите клавишу TAB. Так как «test» ярлык фрагмента кода, фрагмент должен вставляться снова.  
  
## Следующие действия