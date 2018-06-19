---
title: 'Пошаговое руководство: Реализация фрагменты кода | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae260951160bc3d4ed3bb1535f47eb1f33649957
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148692"
---
# <a name="walkthrough-implementing-code-snippets"></a>Пошаговое руководство: Реализация фрагменты кода
Можно создавать фрагменты кода и включить их в редактор расширения, чтобы пользователи расширения можно добавить их в свой собственный код.  
  
 Фрагмент кода представляет собой фрагмент кода или другой текст, который может быть включен в файл. Чтобы просмотреть все фрагменты, которые были зарегистрированы для определенных языков программирования на **средства** меню, нажмите кнопку **Диспетчер фрагментов кода**. Чтобы вставить фрагмент в файле место фрагмента, щелкните правой кнопкой мыши щелкните **вставить фрагмент** или **окружить**, фрагмент, который требуется найти и дважды щелкните его. Нажмите клавишу TAB или SHIFT + TAB для изменения соответствующих частей фрагмента и нажмите клавишу ВВОД или ESC, чтобы принять его. Дополнительные сведения см. в статье [Фрагменты кода](../ide/code-snippets.md).  
  
 Фрагмент кода содержится в XML-файл с расширением SNIPPET расширение имени файла. Фрагмент кода может содержать поля, которые выделены после вставки фрагмента кода, чтобы пользователь мог найти и изменить их. Файл фрагмента кода также предоставляет сведения о **Диспетчер фрагментов кода** , чтобы он мог отображать имени фрагмента в соответствующей категории. Сведения о схеме фрагмента см. в разделе [Справочник по схеме фрагментов кода](../ide/code-snippets-schema-reference.md).  
  
 В этом пошаговом руководстве рассматриваются способы выполнения этих задач:  
  
1.  Создайте и зарегистрируйте фрагменты кода для конкретного языка.  
  
2.  Добавить **вставить фрагмент** команды в контекстное меню.  
  
3.  Реализуйте фрагмент расширения.  
  
 Это пошаговое руководство основано на [Пошаговое руководство: отображение завершение операторов](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-and-registering-code-snippets"></a>Создание и регистрация фрагменты кода  
 Как правило фрагменты кода связаны с зарегистрированного языковой службы. Тем не менее, вам не пришлось бы реализовывать <xref:Microsoft.VisualStudio.Package.LanguageService> регистрируемый фрагментов кода. Вместо этого просто укажите идентификатор GUID в файле фрагмента индекса, а затем использовать одинаковый идентификатор GUID в <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> , добавьте в проект.  
  
 Следующие шаги демонстрируют, как создавать фрагменты кода и связывать их с конкретный идентификатор GUID.  
  
1.  Создайте следующую структуру каталогов:  
  
     **%INSTALLDIR%\TestSnippets\Snippets\1033\\**  
  
     где *% InstallDir %* — папка установки Visual Studio. (Хотя этот путь обычно используется для установки фрагменты кода, можно указать любой путь.)  
  
2.  В папке \1033\ создайте XML-файл и назовите его **TestSnippets.xml**. (Несмотря на то, что это имя обычно используется для файла индекса фрагмента кода, можно указать любое имя, при условии, что он имеет расширение имени файла XML-файла.) Добавьте следующий текст и удалить разделитель GUID и добавлять свои собственные.  
  
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
  
3.  Создать файл в папку фрагментов, назовите его **тестирования**`.snippet`, а затем добавьте следующий текст:  
  
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
  
 Ниже показано, как зарегистрировать фрагментов кода.  
  
#### <a name="to-register-code-snippets-for-a-specific-guid"></a>Чтобы зарегистрировать фрагменты кода для конкретный идентификатор GUID  
  
1.  Откройте **CompletionTest** проекта. Сведения о создании этого проекта см. в разделе [Пошаговое руководство: отображение завершение операторов](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2.  В проекте добавьте ссылки на следующие сборки:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   Microsoft.MSXML  
  
3.  В проекте откройте файл source.extension.vsixmanifest.  
  
4.  Убедитесь, что **активы** вкладка содержит **VsPackage** содержимого типа и что **проекта** присваивается имя проекта.  
  
5.  Выберите проект CompletionTest и в окне свойств задайте **создавать файл Pkgdef** для **true**. Сохраните проект.  
  
6.  Добавьте статическое `SnippetUtilities` класса в проект.  
  
     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  В классе SnippetUtilities определить GUID и присвойте ему значение, используемое в файле SnippetsIndex.xml.  
  
     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  Добавить <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> для `TestCompletionHandler` класса. Этот атрибут можно добавить к любому классу (не статического) public или internal в проекте. (Может потребоваться добавить `using` оператор для пространства имен Microsoft.VisualStudio.Shell.)  
  
     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. Постройте и запустите проект. В экспериментальном экземпляре Visual Studio, которая запускается при выполнении проекта, вы зарегистрировали фрагмента кода должны отображаться в **Диспетчер фрагментов кода** под **TestSnippets** языка.  
  
## <a name="adding-the-insert-snippet-command-to-the-shortcut-menu"></a>Добавление команды вставки фрагмента в контекстное меню  
 **Вставить фрагмент** команда не включена в контекстном меню текстового файла. Таким образом необходимо включить команду.  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Чтобы добавить команду Вставить фрагмент в контекстное меню  
  
1.  Откройте `TestCompletionCommandHandler` файл класса.  
  
     Поскольку этот класс реализует <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, можно активировать **вставить фрагмент** в <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод. Прежде чем включить команду, проверьте, что этот метод не вызывается внутри функции автоматизации так как при **вставить фрагмент** выборе команды, он будет отображать пользовательский интерфейс (UI) средство выбора фрагмента.  
  
     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  Постройте и запустите проект. В экспериментальном экземпляре откройте файл, который имеет расширение имени файла .zzz и щелкните правой кнопкой мыши в любом месте в нем. **Вставить фрагмент** команда должна появиться в контекстном меню.  
  
## <a name="implementing-snippet-expansion-in-the-snippet-picker-ui"></a>Реализация фрагмент расширения в средстве выбора фрагмента пользовательского интерфейса  
 В этом разделе показано, как реализовать расширение фрагмент кода, таким образом, компонент выбора фрагментов пользовательского интерфейса отображается, когда **вставить фрагмент** щелчок контекстного меню. Фрагмент кода, также будет расширен, когда пользователь вводит ярлык фрагмента кода и затем нажимает клавишу TAB.  
  
 Для отображения окна выбора фрагментов пользовательского интерфейса и включение навигации и принятия после вставки фрагмента, используйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод. Вставка, самой обрабатывается <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> метод.  
  
 В реализации расширения фрагмент кода используется устаревший <xref:Microsoft.VisualStudio.TextManager.Interop> интерфейсов. Выполняя перевод текущий редактор классов для устаревшего кода, помните, что стандартные интерфейсы использовать сочетание номера строки и номера столбца для указания местоположения в буфер текста, но текущий классы используют один индекс. Таким образом Если буфер имеет три строки, каждая из которых имеет десять символов (плюс новой строки, которая подсчитывает как один символ), четвертый символ в третьей строке находится в позиции 27 в текущей реализации, но это строка 2, позиции 3 в старой реализации.  
  
#### <a name="to-implement-snippet-expansion"></a>Для реализации расширения фрагмент  
  
1.  Для файла, содержащего `TestCompletionCommandHandler` класса, добавьте следующий `using` инструкции.  
  
     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  Сделать `TestCompletionCommandHandler` Реализуйте класс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> интерфейса.  
  
     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  В `TestCompletionCommandHandlerProvider` класса, импортируйте <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.  
  
     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  Добавьте несколько закрытых полей для интерфейсов расширения кода и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  В конструкторе `TestCompletionCommandHandler` класса, задайте следующие поля.  
  
     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  Для отображения выбора фрагментов, когда пользователь щелкает **вставить фрагмент** команды, добавьте следующий код в <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод. (Чтобы сделать пояснения более удобном для чтения, не содержится Exec() код, который используется для завершения операторов; вместо этого блоки кода добавляются к существующему методу). Добавьте следующий блок кода после кода, который проверяет символ-шаблон.  
  
     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  Если фрагмент содержит поля, которые может быть проведена, расширения сеанса остается открытой, пока не будет явно принимается расширение; Если фрагмент не содержит полей, сеанс закрывается и возвращается в виде `null` по <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> метод. В <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод, после выбора фрагмента кода пользовательского интерфейса, добавленного на предыдущем шаге, добавьте следующий код для обработки фрагмент навигации (при нажатии клавиши TAB или SHIFT + TAB после вставки фрагмента).  
  
     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  Чтобы вставить фрагмент кода, когда пользователь вводит соответствующий ярлык и затем нажимает клавишу TAB, добавьте код в <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод. Закрытый метод, который вставляет фрагмент будет отображен на более позднем этапе. Добавьте следующий код после перемещения кода, добавленного на предыдущем шаге.  
  
     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. Реализуйте методы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> интерфейса. В этой реализации являются только методы, представляющие интерес <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Другие методы просто вернет <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. Выполните метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Вспомогательный метод, который фактически вставляет расширения по будет рассматриваться позже. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Сведения строки и столбца, который можно получить из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. Приведенный ниже закрытый метод вставляет фрагмент кода, либо на основе ярлык или заголовок и путь. Затем он вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> метод с помощью фрагмента.  
  
     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## <a name="building-and-testing-code-snippet-expansion"></a>Построение и тестирование расширения фрагмента кода  
 Можно проверить ли работает фрагмент расширения в проекте.  
  
1.  Постройте решение. При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
2.  Откройте текстовый файл и введите текст.  
  
3.  Щелкните правой кнопкой мыши где-нибудь в тексте, а затем нажмите кнопку **вставить фрагмент**.  
  
4.  Выбор фрагмента, пользовательский Интерфейс должен выглядеть с всплывающее окно с сообщением **поля замены тестов**. Дважды щелкните всплывающего окна.  
  
     Следующий фрагмент кода следует вставить.  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     Не нажимайте клавишу ВВОД или ESC.  
  
5.  Нажмите клавишу TAB и SHIFT + TAB для переключения между «первый» и «секунду».  
  
6.  Примите вставку нажатием клавиши ВВОД или ESC.  
  
7.  В другой его части текста введите «test» и нажмите клавишу TAB. Так как «test» ярлык фрагмента кода, еще раз следует вставить фрагмент.  
  
## <a name="next-steps"></a>Следующие шаги