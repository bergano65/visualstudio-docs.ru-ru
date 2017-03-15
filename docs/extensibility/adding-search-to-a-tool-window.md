---
title: "Добавление поиска в окне инструментов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
caps.latest.revision: 38
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: bca8c87d4f7d89d491fab13e1a511febce81d3d8
ms.openlocfilehash: 845bbc5c34280f7ceafcaa3d763065f6d73388fe
ms.lasthandoff: 02/22/2017

---
# <a name="adding-search-to-a-tool-window"></a>Добавление поиска окно инструментов
При создании или обновлении окна средства расширения, в Visual Studio можно добавить те же функциональные возможности поиска, который отображается в другом месте. Эти функции включают следующие компоненты:  
  
-   Поле поиска, которое всегда находится в пользовательские области панели инструментов.  
  
-   Индикатор хода выполнения, который появляется в поле «Поиск».  
  
-   Возможность Показать результаты, как только ввод каждого символа (мгновенного поиска) или только после нажатия клавиши Enter (поиск по запросу).  
  
-   Список терминов, для которых вы сделали поиск наиболее недавно.  
  
-   Возможность фильтрации по отдельным полям или аспектов целевых объектов поиска.  
  
 В этом пошаговом руководстве вы узнаете, как выполнять следующие задачи:  
  
1.  Создайте проект VSPackage.  
  
2.  Создайте окно инструментов, которое содержит UserControl с текстового поля только для чтения.  
  
3.  Добавьте поле поиска окно инструментов.  
  
4.  Реализация поиска.  
  
5.  Включите мгновенный поиск и отображение индикатора выполнения.  
  
6.  Добавить **с учетом регистра** параметр.  
  
7.  Добавить **искать только даже строки** фильтра.  
  
## <a name="to-create-a-vsix-project"></a>Создание проекта VSIX  
  
1.  Создайте проект VSIX с именем `TestToolWindowSearch` с окном инструмента с именем **TestSearch**. Если понадобится помощь, это [создания расширения с окном инструмента](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="to-create-a-tool-window"></a>Для создания окна инструментов  
  
1.  В `TestToolWindowSearch` проекта, откройте файл TestSearchControl.xaml.  
  
2.  Замените существующий `<StackPanel>` блок с следующий блок, который добавляет только для чтения <xref:System.Windows.Controls.TextBox>для <xref:System.Windows.Controls.UserControl>в окне инструментов.</xref:System.Windows.Controls.UserControl> </xref:System.Windows.Controls.TextBox>  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  В файле TestSearchControl.xaml.cs добавьте следующий оператор using:  
  
    ```c#  
    using System.Text;  
    ```  
  
4.  Удалить `button1_Click()` метод.  
  
     В **TestSearchControl** добавьте следующий код.  
  
     Этот код добавляет открытую <xref:System.Windows.Controls.TextBox>свойство с именем **SearchResultsTextBox** и открытые строковое свойство с именем **SearchContent**.</xref:System.Windows.Controls.TextBox> В конструкторе SearchResultsTextBox имеет значение в текстовое поле и SearchContent инициализируется набор строк, разделенных символом новой строки. Содержимое текстового поля также инициализируется в набор строк.  
  
    ```c#  
    public partial class TestSearchControl : UserControl  
    {  
        public TextBox SearchResultsTextBox { get; set; }  
        public string SearchContent { get; set; }  
  
        public TestSearchControl()  
        {  
            InitializeComponent();  
  
            this.SearchResultsTextBox = resultsTextBox;  
            this.SearchContent = BuildContent();  
  
            this.SearchResultsTextBox.Text = this.SearchContent;  
        }  
  
        private string BuildContent()  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.AppendLine("1 go");  
            sb.AppendLine("2 good");  
            sb.AppendLine("3 Go");  
            sb.AppendLine("4 Good");  
            sb.AppendLine("5 goodbye");  
            sb.AppendLine("6 Goodbye");  
  
            return sb.ToString();  
        }  
    }  
    ```  
  
     [!code-cs[#1 ToolWindowSearch](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs) ] 
     [!code-vb [ToolWindowSearch&#1;](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр Visual Studio.  
  
6.  В строке меню выберите **представление**, **другие окна**, **TestSearch**.  
  
     Появится окно средства, но элемент управления поиском еще не отображается.  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>Чтобы добавить поле поиска в окно средства  
  
1.  В файле TestSearch.cs добавьте следующий код в `TestSearch` класса. Код переопределяет <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>Свойства, чтобы метод доступа get возвращает `true`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>  
  
     Чтобы включить поиск, необходимо переопределить <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>свойство.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>Реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch>и предоставляет стандартную реализацию, которая не включает поиск.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> </xref:Microsoft.VisualStudio.Shell.ToolWindowPane>  
  
    ```c#  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
3.  В экспериментальном экземпляре Visual Studio, откройте **TestSearch**.  
  
     В верхней части окна средства, появляется элемент управления поиска с **поиска** водяного знака и значок увеличение стекла. Тем не менее поиск не работает, так как процесс поиска не реализован.  
  
## <a name="to-add-the-search-implementation"></a>Чтобы добавить реализацию поиска  
 При включении поиска <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, как в предыдущей процедуре, то окно инструментов создает узел поиска.</xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Этот узел настраивает и управляет поиска процессов, которые всегда выполняется в фоновом потоке. Поскольку <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>класс управляет созданием узла поиска и параметра вверх поиска, необходимо только создать задачу поиска и предоставить метод поиска.</xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Поиск выполняется в фоновом потоке, а вызовы элемент управления окна инструментов, происходят в потоке пользовательского интерфейса. Таким образом, необходимо использовать <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>метода для управления все вызовы, сделанные в работе с элементом управления.</xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>  
  
1.  Добавьте следующий код в файле TestSearch.cs `using` инструкции:  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Runtime.InteropServices;  
    using System.Text;  
    using System.Windows.Controls;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
2.  В `TestSearch` добавьте следующий код, который выполняет следующие действия:  
  
    -   Переопределяет <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch>метод для создания задачи поиска.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch>  
  
    -   Переопределяет <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>способ восстановления состояния надписи.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> Этот метод вызывается, когда пользователь отменяет задачу поиска и когда пользователь задает или отменяет параметры или фильтры. Оба <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>и <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>вызываются в потоке пользовательского интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> Таким образом, не требуется доступ к текстовое поле с помощью параметра <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>метод.</xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>  
  
    -   Создает класс с именем `TestSearchTask` , наследуемый от <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, который предоставляет реализацию по умолчанию <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask> </xref:Microsoft.VisualStudio.Shell.VsSearchTask>  
  
         В `TestSearchTask`, конструктор задает закрытое поле, которое ссылается на окно инструментов. Чтобы предоставить метод search, переопределить <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>и <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A>методы.</xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> </xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>Метод в том, где реализована процесс поиска.</xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> Этот процесс включает выполнение поиска и отображение результатов поиска в текстовом поле вызова реализации базового класса этого метода для отчета о завершении поиска.  
  
    ```c#  
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)  
    {  
        if (pSearchQuery == null || pSearchCallback == null)  
            return null;  
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);  
    }  
  
    public override void ClearSearch()  
    {  
        TestSearchControl control = (TestSearchControl)this.Content;  
        control.SearchResultsTextBox.Text = control.SearchContent;  
    }  
  
    internal class TestSearchTask : VsSearchTask  
    {  
        private TestSearch m_toolWindow;  
  
        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)  
            : base(dwCookie, pSearchQuery, pSearchCallback)  
        {  
            m_toolWindow = toolwindow;  
        }  
  
        protected override void OnStartSearch()  
        {  
            // Use the original content of the text box as the target of the search.   
            var separator = new string[] { Environment.NewLine };  
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;  
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);  
  
            // Get the search option.   
            bool matchCase = false;  
            // matchCase = m_toolWindow.MatchCaseOption.Value;   
  
                // Set variables that are used in the finally block.  
                StringBuilder sb = new StringBuilder("");  
                uint resultCount = 0;  
                this.ErrorCode = VSConstants.S_OK;  
  
                try  
                {  
                    string searchString = this.SearchQuery.SearchString;  
  
                    // Determine the results.   
                    uint progress = 0;  
                    foreach (string line in contentArr)  
                    {  
                        if (matchCase == true)  
                        {  
                            if (line.Contains(searchString))  
                            {  
                                sb.AppendLine(line);  
                                resultCount++;  
                            }  
                        }  
                        else  
                            {  
                                if (line.ToLower().Contains(searchString.ToLower()))  
                                {  
                                    sb.AppendLine(line);  
                                    resultCount++;  
                                }  
                            }  
  
                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));   
  
                            // Uncomment the following line to demonstrate the progress bar.   
                            // System.Threading.Thread.Sleep(100);  
                        }  
                    }  
                    catch (Exception e)  
                    {  
                        this.ErrorCode = VSConstants.E_FAIL;  
                    }  
                    finally  
                    {  
                        ThreadHelper.Generic.Invoke(() =>  
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
                        this.SearchResults = resultCount;  
                    }  
  
            // Call the implementation of this method in the base class.   
            // This sets the task status to complete and reports task completion.   
            base.OnStartSearch();  
        }  
  
        protected override void OnStopSearch()  
        {  
            this.SearchResults = 0;  
        }  
    }  
    ```  
  
3.  Проверьте реализацию поиска, выполнив следующие действия:  
  
    1.  Перестройте проект и запустить отладку.  
  
    2.  В экспериментальном экземпляре Visual Studio снова откройте окно инструментов, введите текст поиска в окне поиска и нажмите клавишу ВВОД.  
  
         Отображаются правильные результаты.  
  
## <a name="to-customize-the-search-behavior"></a>Для настройки поведения поиска  
 Изменив параметры поиска, можно внести ряд изменений в внешний вид элемента управления для поиска и способ выполнения поиска. Например можно изменить водяной знак (по умолчанию текст, отображаемый в поле «Поиск»), минимальное и максимальную ширину элемента управления поиска и нужно ли отображать индикатор хода выполнения. Можно также изменить точку в какие результаты поиска начнут отображаться (по запросу или мгновенного поиска) и нужно ли отображать список терминов, для которых недавно поиск. Полный список параметров можно найти в <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>класс.</xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>  
  
1.  В файле TestSearch.cs добавьте следующий код в `TestSearch` класса. Этот код позволяет мгновенный поиск вместо поиска по требованию (это значит, что пользователю не нужно нажмите клавишу ВВОД). Код переопределяет `ProvideSearchSettings` метод `TestSearch` класса, который необходимо изменить параметры по умолчанию.  
  
    ```c#  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  Проверить новый параметр, при перестройке решения и перезапуска отладчика.  
  
     Результаты поиска отображаются каждый раз при вводе символа в поле поиска.  
  
3.  В `ProvideSearchSettings` метод, добавьте следующую строку, которая позволяет отображать индикатор хода выполнения.  
  
    ```c#  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,   
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);  
    }  
    ```  
  
     Для отображения индикатора хода выполнения должно сообщаться. Чтобы сообщить о ходе выполнения, раскомментируйте следующий код в `OnStartSearch` метод `TestSearchTask` класса:  
  
    ```c#  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  Снизить скорость обработки недостаточно, ход выполнения отображается панель, раскомментируйте следующую строку в `OnStartSearch` метод `TestSearchTask` класса:  
  
    ```c#  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  Проверьте новые параметры, при перестройке решения и начало debugb.  
  
     Индикатор отображается в окне «Поиск» (как синей линией под текстовым полем поиска) каждый раз, при выполнении поиска.  
  
## <a name="to-enable-users-to-refine-their-searches"></a>Чтобы предоставить пользователям возможность уточнять поиск  
 Можно разрешить пользователям уточнить поиск с помощью параметров, таких как **с учетом регистра** или **слово целиком**. Параметры могут быть boolean, которые отображаются как флажки или команды, которые отображаются в виде кнопок. В данном пошаговом руководстве вы создадите логического параметра.  
  
1.  В файле TestSearch.cs добавьте следующий код в `TestSearch` класса. Код переопределяет `SearchOptionsEnum` метод, который позволяет определить, является ли данный параметр и отключение поиска реализации. Код в `SearchOptionsEnum` добавляет возможность с учетом регистра для <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions>перечислителя.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> Параметр, чтобы учитывать регистр также доступны в качестве `MatchCaseOption` свойство.  
  
    ```c#  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
        {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
2.  В `TestSearchTask` класс, раскомментируйте строку matchCase в `OnStartSearch` метод:  
  
    ```c#  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
         {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
3.  Проверьте параметр:  
  
    1.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
    2.  В окне инструментов выберите стрелку вниз справа от текстового поля.  
  
         **С учетом регистра** отображается флажок.  
  
    3.  Выберите **с учетом регистра** флажок, а затем выполнять некоторые запросы поиска.  
  
## <a name="to-add-a-search-filter"></a>Чтобы добавить фильтр поиска  
 Можно добавить фильтры поиска, позволяющие пользователям уточнить набор целевых объектов поиска. Например можно выполнить фильтрацию файлов в проводнике, даты, на которых они были последнего изменения и расширения имен файлов. В этом пошаговом руководстве вы добавите фильтра даже только для строк. Когда пользователь выбирает фильтр, поиск узла добавляет строки, указываемые поискового запроса. Затем можно определить эти строки в метод поиска и фильтрации целевых объектов поиска соответствующим образом.  
  
1.  В файле TestSearch.cs добавьте следующий код в `TestSearch` класса. Этот код реализует `SearchFiltersEnum` , добавив <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>, задающий для фильтрации результатов поиска, чтобы отображались только строки, даже.</xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>  
  
    ```c#  
    public override IVsEnumWindowSearchFilters SearchFiltersEnum  
    {  
        get  
        {  
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();  
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));  
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;  
        }  
    }  
  
    ```  
  
     Теперь элемент управления поиска отображает фильтр поиска `Search even lines only`. Когда пользователь выбирает фильтр, строка `lines:"even"` отображается в поле поиска. В то же время, как фильтр могут отображаться другие критерии поиска. Строки поиска может появляться до фильтра, фильтр или оба.  
  
2.  В файле TestSearch.cs добавьте следующие методы для `TestSearchTask` класс, который находится в `TestSearch` класса. Эти методы поддерживают `OnStartSearch` метод, который необходимо изменить на следующем шаге.  
  
    ```c#  
    private string RemoveFromString(string origString, string stringToRemove)  
    {  
        int index = origString.IndexOf(stringToRemove);  
        if (index == -1)  
            return origString;  
        else   
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();  
    }  
  
    private string[] GetEvenItems(string[] contentArr)  
    {  
        int length = contentArr.Length / 2;  
        string[] evenContentArr = new string[length];  
  
        int indexB = 0;  
        for (int index = 1; index < contentArr.Length; index += 2)  
        {  
            evenContentArr[indexB] = contentArr[index];  
            indexB++;  
        }  
  
        return evenContentArr;  
    }  
    ```  
  
3.  В `TestSearchTask` класса, обновите `OnStartSearch` метод следующим кодом. Это изменение обновляет код для поддержки фильтра.  
  
    ```c#  
    protected override void OnStartSearch()  
    {  
        // Use the original content of the text box as the target of the search.   
        var separator = new string[] { Environment.NewLine };  
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);  
  
        // Get the search option.   
        bool matchCase = false;  
        matchCase = m_toolWindow.MatchCaseOption.Value;  
  
        // Set variables that are used in the finally block.  
        StringBuilder sb = new StringBuilder("");  
        uint resultCount = 0;  
        this.ErrorCode = VSConstants.S_OK;  
  
        try  
        {  
            string searchString = this.SearchQuery.SearchString;  
  
            // If the search string contains the filter string, filter the content array.   
            string filterString = "lines:\"even\"";  
  
            if (this.SearchQuery.SearchString.Contains(filterString))  
            {  
                // Retain only the even items in the array.  
                contentArr = GetEvenItems(contentArr);  
  
                // Remove 'lines:"even"' from the search string.  
                searchString = RemoveFromString(searchString, filterString);  
            }  
  
            // Determine the results.   
            uint progress = 0;  
            foreach (string line in contentArr)  
            {  
                if (matchCase == true)  
                {  
                    if (line.Contains(searchString))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
                else  
                {  
                    if (line.ToLower().Contains(searchString.ToLower()))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
  
                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
  
                // Uncomment the following line to demonstrate the progress bar.   
                // System.Threading.Thread.Sleep(100);  
            }  
        }  
        catch (Exception e)  
        {  
            this.ErrorCode = VSConstants.E_FAIL;  
        }  
        finally  
        {  
            ThreadHelper.Generic.Invoke(() =>  
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
            this.SearchResults = resultCount;  
        }  
  
        // Call the implementation of this method in the base class.   
        // This sets the task status to complete and reports task completion.   
        base.OnStartSearch();  
    }  
    ```  
  
4.  Тестирование кода.  
  
5.  Выполните сборку решения и запустите отладку. В экспериментальном экземпляре Visual Studio откройте окно инструментов и нажмите кнопку со стрелкой вниз на элементе управления поиска.  
  
     **С учетом регистра** флажок и **искать только даже строки** отображаются фильтра.  
  
6.  Выберите фильтр.  
  
     Поле поиска содержит **строк: «четными»**, и отображаются следующие результаты:  
  
     Хороший&2;  
  
     Хорошее&4;  
  
     6 до свидания  
  
7.  Удалить `lines:"even"` в поле поиска выберите **с учетом регистра** флажок, а затем введите `g` в поле поиска.  
  
     Отображаются следующие результаты:  
  
     Переход на&1;  
  
     Хороший&2;  
  
     5 до свидания  
  
8.  Нажмите кнопку X справа от поля поиска.  
  
     Поиск очищается и отображается исходное содержимое. Тем не менее **с учетом регистра** по-прежнему установлен флажок.
