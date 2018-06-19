---
title: Добавление в окно инструментов поиска | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f3b5aa52968be5a2efcf88d7a31505d94f97aaec
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2018
ms.locfileid: "32032074"
---
# <a name="adding-search-to-a-tool-window"></a>Добавление поиска в окно инструментов
При создании или обновлении расширения окна инструментов, можно добавить те же функциональные возможности поиска, которое отображается в другом месте в Visual Studio. Эти функции включают следующие компоненты:  
  
-   Поле поиска, которое всегда расположено в пользовательской области панели инструментов.  
  
-   Индикатор хода выполнения, которое накладывается на само поле поиска.  
  
-   Возможность отображения результатов сразу после ввода каждого символа (быстрого поиска) или только после нажатия клавиши ВВОД (поиск по запросу).  
  
-   Список терминов, для которых выполнения поиска самой последней.  
  
-   Возможность фильтрации при поисках по определенным полям или аспекты поиска целевых объектов.  
  
 Перечисленные в этом пошаговом руководстве, вы узнаете, как для выполнения следующих задач:  
  
1.  Создайте проект VSPackage.  
  
2.  Создайте окно инструментов, содержащий пользовательского элемента управления с помощью текстового поля только для чтения.  
  
3.  Добавьте поле поиска в окне инструментов.  
  
4.  Добавьте реализацию поиска.  
  
5.  Включение быстрого поиска и отображения индикатора выполнения.  
  
6.  Добавить **с учетом регистра** параметр.  
  
7.  Добавить **искать только даже строки** фильтра.  
  
## <a name="to-create-a-vsix-project"></a>Создание проекта VSIX  
  
1.  Создайте проект VSIX с именем `TestToolWindowSearch` с окно инструментов с именем **TestSearch**. Если вам нужна помощь, таким образом, в разделе [создания расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="to-create-a-tool-window"></a>Чтобы создать окно инструментов  
  
1.  В `TestToolWindowSearch` проекта, откройте файл TestSearchControl.xaml.  
  
2.  Заменить существующий `<StackPanel>` блок с следующий блок, который добавляет только для чтения <xref:System.Windows.Controls.TextBox> для <xref:System.Windows.Controls.UserControl> в окне инструментов.  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  В файле TestSearchControl.xaml.cs добавьте следующие инструкции с помощью:  
  
    ```csharp  
    using System.Text;  
    ```  
  
4.  Удалить `button1_Click()` метод.  
  
     В **TestSearchControl** класса, добавьте следующий код.  
  
     Этот код добавляет открытую <xref:System.Windows.Controls.TextBox> свойство с именем **SearchResultsTextBox** и строку открытого свойства с именем **SearchContent**. В конструкторе SearchResultsTextBox имеет значение в текстовое поле и SearchContent инициализируется набор строк, разделенных символом новой строки. Содержимое текстового поля также инициализируется в набор строк.  
  
     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр Visual Studio.  
  
6.  В строке меню выберите **представление**, **другие окна**, **TestSearch**.  
  
     Появится окно инструментов, но элемент управления поиска еще не отображается.  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>Чтобы добавить поле поиска для окна инструментов  
  
1.  В файле TestSearch.cs добавьте следующий код в `TestSearch` класса. Код переопределяет <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> свойство так, что метод доступа get возвращает `true`.  
  
     Чтобы включить поиск, необходимо переопределить <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> свойство. <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Класс реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> и обеспечивает реализацию по умолчанию, которая не включает поиска.  
  
    ```csharp  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
3.  В экспериментальном экземпляре Visual Studio, откройте **TestSearch**.  
  
     В верхней части окна инструментов, элемент управления поиска отображается с **поиска** водяного знака и значок увеличение стекла. Тем не менее поиск не работает еще, так как процесс поиска еще не реализовано.  
  
## <a name="to-add-the-search-implementation"></a>Добавление реализации поиска  
 При включении поиска на <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, как в предыдущей процедуре, в окне инструментов создает узла поиска. Этот узел настраивает и управляет поиска процессов, которые происходят в фоновом потоке. Поскольку <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> класс управляет созданием узла поиска и параметра вверх поиска, требуется только создать задачу поиска и предоставляют способ поиска. Процесс поиска будет выполняться в фоновом потоке и вызовы элемент управления окна инструментов, происходят в потоке пользовательского интерфейса. Таким образом, необходимо использовать <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> метод для управления все вызовы, сделанные в работе с элементом управления.  
  
1.  Добавьте следующие строки в файле TestSearch.cs `using` инструкции:  
  
    ```csharp  
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
  
    -   Переопределяет <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> метод для создания задачи поиска.  
  
    -   Переопределяет <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> метод, чтобы восстановить состояние текстового поля. Этот метод вызывается, когда пользователь отменяет задачи поиска и когда пользователь задает или отменяет параметры или фильтры. Оба <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> вызываются в потоке пользовательского интерфейса. Таким образом, не требуется доступ к текстовое поле с помощью параметра <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> метод.  
  
    -   Создает класс с именем `TestSearchTask` , наследуемый от <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, который предоставляет реализацию по умолчанию <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.  
  
         В `TestSearchTask`, конструктор задает закрытое поле, которое ссылается на окно инструментов. Чтобы предоставить метод поиска, переопределите <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> и <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> методы. <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> Метод в том, где реализована процесс поиска. Этот процесс включает выполнение поиска и отображения результатов поиска в текстовом поле вызова реализации базового класса этот метод для сообщения о завершении поиска.  
  
    ```csharp  
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
  
    1.  Перестройте проект и начните отладку.  
  
    2.  В экспериментальном экземпляре Visual Studio снова откройте окно инструментов, введите текст поиска в окне поиска и нажмите клавишу ВВОД.  
  
         Должны появиться правильные результаты.  
  
## <a name="to-customize-the-search-behavior"></a>Для настройки поведения поиска  
 Можно изменить параметры поиска, можно вносить различные изменения в внешний вид элемента управления для поиска и способ выполнения поиска. Например можно изменить водяной знак (по умолчанию текст, отображаемый в поле поиска), минимального и максимальную ширину элемента управления поиска и следует ли отображать индикатор хода выполнения. Можно также изменить в момент какие результаты поиска начнут отображаться (по запросу или быстрого поиска) и необходимость отображения списка условий, для которых недавно поиск. Можно найти полный список параметров в <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> класса.  
  
1.  В файле TestSearch.cs добавьте следующий код в `TestSearch` класса. Этот код позволяет быстрого поиска вместо поиска по требованию (это значит, что пользователю не нужно нажать клавишу ВВОД). Код переопределяет `ProvideSearchSettings` метод `TestSearch` класса, который необходимо изменить параметры по умолчанию.  
  
    ```csharp  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  Проверить новый параметр, при перестройке решения и перезапуска отладчика.  
  
     Результаты поиска отображаются при каждом вводе символа в поле поиска.  
  
3.  В `ProvideSearchSettings` метода, добавьте следующую строку, которая позволяет отображать индикатор хода выполнения.  
  
    ```csharp  
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
  
     Отображается индикатор выполнения должны считаться ход выполнения. Чтобы сообщить о ходе выполнения, раскомментируйте следующий код в `OnStartSearch` метод `TestSearchTask` класса:  
  
    ```csharp  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  Снизить скорость обработки недостаточно, ход выполнения отображается панель, раскомментируйте следующую строку в `OnStartSearch` метод `TestSearchTask` класса:  
  
    ```csharp  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  Проверьте новые параметры, при перестройке решения и начните отладку.  
  
     Индикатор выполнения отображается в окне поиска (как синюю линию под текстовым полем поиска) каждый раз, при выполнении поиска.  
  
## <a name="to-enable-users-to-refine-their-searches"></a>Чтобы пользователи могли уточнять поиск  
 Можно разрешить пользователям уточнять поиск с помощью параметров, таких как **с учетом регистра** или **слово целиком**. Параметры могут быть boolean, которые отображаются как флажки или команды, которые отображаются в виде кнопок. В этом пошаговом руководстве вы создадите логического параметра.  
  
1.  В файле TestSearch.cs добавьте следующий код в `TestSearch` класса. Код переопределяет `SearchOptionsEnum` метод, который позволяет определить, является ли указанный параметр и отключение поиска реализации. Код в `SearchOptionsEnum` добавляет возможность с учетом регистра для <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> перечислителя. Параметр, чтобы учитывать регистр также доступны в качестве `MatchCaseOption` свойство.  
  
    ```csharp  
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
  
2.  В `TestSearchTask` класса, раскомментируйте следующую строку в `OnStartSearch` метод:  
  
    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```
  
3.  Проверьте параметр:  
  
    1.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
    2.  В окне инструментов выберите стрелку вниз справа от текстового поля.  
  
         **С учетом регистра** отображается флажок.  
  
    3.  Выберите **с учетом регистра** флажок, а затем выполнять некоторые запросы поиска.  
  
## <a name="to-add-a-search-filter"></a>Чтобы добавить фильтр поиска  
 Можно добавить фильтры поиска, позволяющие пользователям уточнить набор целевых объектов для поиска. Например можно выполнить фильтрацию файлов в проводнике по датам, в которых они были последнего изменения и их расширения. В этом пошаговом руководстве вы добавите фильтра даже только для строк. При выборе этого фильтра, узла поиска добавляет строки, указанные в запросе поиска. Можно определить эти строки внутри метода поиска и фильтрации поиска целевые объекты соответствующим образом.  
  
1.  В файле TestSearch.cs добавьте следующий код в `TestSearch` класса. Этот код реализует `SearchFiltersEnum` путем добавления <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> , указывающий для фильтрации результатов поиска, чтобы отображались только строки, даже.  
  
    ```csharp  
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
  
     Теперь элемент управления поиска отображает фильтр поиска `Search even lines only`. Когда пользователь нажмет фильтра, строка `lines:"even"` отображается в поле поиска. В то же время, как фильтр могут отображаться другие критерии поиска. Строки поиска может отображаться до фильтра, после фильтра или оба.  
  
2.  В файле TestSearch.cs добавьте следующие методы для `TestSearchTask` класс, который находится в `TestSearch` класса. Эти методы поддерживают `OnStartSearch` метод, который будет изменен на следующем шаге.  
  
    ```csharp  
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
  
    ```csharp  
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
  
5.  Выполните сборку решения и запустите отладку. В экспериментальном экземпляре Visual Studio откройте окно инструментов и затем нажмите стрелку вниз на элемент управления поиска.  
  
     **С учетом регистра** флажок и **искать только даже строки** фильтры отображаются.  
  
6.  Выберите фильтр.  
  
     Окно поиска содержит **строки: «даже»**, и отображаются следующие результаты:  
  
     Хороший 2  
  
     Хорошее 4  
  
     6 до свидания  
  
7.  Удалить `lines:"even"` в поле поиска выберите **с учетом регистра** флажок, а затем введите `g` в поле поиска.  
  
     Отображаются следующие результаты:  
  
     Перейдите на 1  
  
     Хороший 2  
  
     5 до свидания  
  
8.  Нажмите кнопку X справа от поля поиска.  
  
     Поиск снят, а исходное содержимое отображается. Тем не менее **с учетом регистра** по-прежнему установлен флажок.