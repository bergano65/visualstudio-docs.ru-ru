---
title: Добавление поиска в окно инструментов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8df7dc811a9e4115998e3d423d749edfbdb62278
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54943777"
---
# <a name="add-search-to-a-tool-window"></a>Добавление поиска в окно инструментов
При создании или обновлении расширения окна инструментов, можно добавить функций поиска, появляющийся в Visual Studio. Эта функция включает в себя следующие компоненты:  
  
-   Поле поиска, которое всегда находится в настраиваемые области панели инструментов.  
  
-   Индикатор хода выполнения, который появляется в поле поиска, сам.  
  
-   Возможность Показать результаты, как только вы введете каждый символ (мгновенного поиска), или только в том случае, когда вы выберете **ввод** ключ (поиск по запросу).  
  
-   Список терминов, для которых выполнялся недавно.  
  
-   Возможность фильтрации по отдельным полям или аспекты поиска целевых объектов.  
  
Перечисленные в этом пошаговом руководстве, вы узнаете, как выполнять следующие задачи:  
  
1.  Создайте проект VSPackage.  
  
2.  Создайте окно инструментов, содержащий элемент управления UserControl с текстовым полем только для чтения.  
  
3.  Добавление поля поиска для окна инструментов.  
  
4.  Добавьте реализацию поиска.  
  
5.  Включите мгновенного поиска и отображения индикатора выполнения.  
  
6.  Добавить **учитывать регистр** параметр.  
  
7.  Добавить **искать только даже строки** фильтра.  
  
## <a name="to-create-a-vsix-project"></a>Создание проекта VSIX  
  
1.  Создайте проект VSIX с именем `TestToolWindowSearch` с окном инструментов с именем **TestSearch**. Если вам нужна помощь, таким образом, см. в разделе [создания расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="to-create-a-tool-window"></a>Создать окно инструментов  
  
1.  В `TestToolWindowSearch` откройте проект *TestSearchControl.xaml* файла.  
  
2.  Замените существующий `<StackPanel>` блока с помощью приведенного ниже, который добавляет доступное только для чтения <xref:System.Windows.Controls.TextBox> для <xref:System.Windows.Controls.UserControl> в окне инструментов.  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  В *TestSearchControl.xaml.cs* файл, добавьте следующий оператор using:  
  
    ```csharp  
    using System.Text;  
    ```  
  
4.  Удалить `button1_Click()` метод.  
  
     В **TestSearchControl** класса, добавьте следующий код.  
  
     Этот код добавляет открытую <xref:System.Windows.Controls.TextBox> свойство с именем **SearchResultsTextBox** и общедоступное строковое свойство с именем **SearchContent**. В конструкторе SearchResultsTextBox имеет значение в текстовое поле и SearchContent инициализируется набор строк, разделенных символом новой строки. Содержимое текстового поля также инициализируется набор строковых значений.  
  
     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр Visual Studio.  
  
6.  В строке меню выберите **представление** > **Other Windows** > **TestSearch**.  
  
     Оно отображается, но пока не отображается в элементе управления поиском.  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>Чтобы добавить поле для поиска окно инструментов  
  
1.  В *TestSearch.cs* добавьте следующий код, чтобы `TestSearch` класса. Код переопределяет <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> свойство так, что возвращает метод доступа get `true`.  
  
     Чтобы включить поиск, необходимо переопределить <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> свойство. <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Класс реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> и предоставляет реализацию по умолчанию, которая не позволяет использовать поиск.  
  
    ```csharp  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
3.  В экспериментальном экземпляре Visual Studio, откройте **TestSearch**.  
  
     В верхней части окна инструментов, появляется элемент управления поиска с **поиска** водяного знака и значок увеличение аварийного доступа. Тем не менее поиск не работает еще, так как процесс поиска не реализован.  
  
## <a name="to-add-the-search-implementation"></a>Чтобы добавить реализацию поиска  
 При включении поиска на <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, как в предыдущей процедуре, окна инструментов создает узел поиска. Этот узел настраивает и управляет процессами поиска, они всегда выполняются в фоновом потоке. Так как <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> класс управляет созданием узел поиска и параметра вверх поиска, требуется только создать задачу поиска и предоставить метод поиска. Процесс поиска выполняется в фоновом потоке и вызовы к элементу управления окна инструмента, происходят в потоке пользовательского интерфейса. Таким образом, необходимо использовать <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> метод для управления все вызовы, выполненные в работе с элементом управления.  
  
1.  В *TestSearch.cs* добавьте следующие `using` инструкции:  
  
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
  
    -   Переопределяет <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> метод, чтобы создать задачу поиска.  
  
    -   Переопределяет <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> метод, чтобы восстановить состояние текстового поля. Этот метод вызывается, когда пользователь отменяет задачу поиска и когда пользователь задает или отменяет параметры или фильтры. Оба <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> вызываются в потоке пользовательского интерфейса. Таким образом, вам не требуется доступ к текстовое поле с помощью параметра <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> метод.  
  
    -   Создает класс с именем `TestSearchTask` , наследуемый от <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, который предоставляет реализацию по умолчанию <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.  
  
         В `TestSearchTask`, конструктор задает закрытое поле, которое ссылается на окно инструментов. Чтобы предоставить метод поиска, переопределите <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> и <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> методы. <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> Метод выполняется реализация процесс поиска. Этот процесс включает поиска и отображения результатов поиска в текстовом поле вызова реализации базового класса этого метода, чтобы сообщить о завершении поиска.  
  
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
  
    2.  В экспериментальном экземпляре Visual Studio, откройте окно инструментов снова, введите текст поиска в окне поиска и нажмите кнопку **ввод**.  
  
         Правильный результат должен выглядеть.  
  
## <a name="to-customize-the-search-behavior"></a>Для настройки поведения поиска  
 Можно изменить параметры поиска, можно внести ряд изменений в вид элемента управления поиска и способ выполнения поиска. Например можно изменить водяной знак (по умолчанию текст, отображаемый в поле поиска), минимальная и максимальная ширина элемента управления поиском и нужно ли отображать индикатор хода выполнения. Можно также изменить точку, в какие результаты поиска запустить отображаются (по запросу или мгновенного поиска) и нужно ли отображать список терминов, для которых вы недавно выполнялся поиск. Можно найти полный список параметров в <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> класса.  
  
1.  В * TestSearch.cs* добавьте следующий код, чтобы `TestSearch` класса. Этот код позволяет мгновенного поиска вместо поиска по запросу (это значит, что пользователю не нужно щелкните **ввод**). Код переопределяет `ProvideSearchSettings` метод в `TestSearch` класс, который необходимо изменить параметры по умолчанию.  
  
    ```csharp  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  Проверить новый параметр повторная сборка решения и не перезапуская отладчик.  
  
     Результаты поиска отображаются каждый раз при вводе символа в поле поиска.  
  
3.  В `ProvideSearchSettings` метод, добавьте следующую строку, которая позволяет отображать индикатор хода выполнения.  
  
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
  
     Отображается индикатор хода выполнения должны подтверждать ход выполнения. Чтобы сообщить о ходе выполнения, раскомментируйте следующий код в `OnStartSearch` метод `TestSearchTask` класса:  
  
    ```csharp  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  Снизить скорость обработки недостаточно, хода выполнения отображается панель, раскомментируйте следующую строку в `OnStartSearch` метод `TestSearchTask` класса:  
  
    ```csharp  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  Проверьте новые параметры, повторная сборка решения и начните отладку.  
  
     Индикатор хода выполнения отображается в окне поиска (в виде синей линией под текстовым полем поиска) каждый раз, при выполнении поиска.  
  
## <a name="to-enable-users-to-refine-their-searches"></a>Чтобы пользователи могли уточнять поиск  
 Можно разрешить пользователям уточнить поиск с помощью параметров, таких как **учитывать регистр** или **слово целиком**. Параметры могут быть логическое, которые отображаются как флажки или команды, которые отображаются в виде кнопок. В этом пошаговом руководстве вы создадите логический параметр.  
  
1.  В *TestSearch.cs* добавьте следующий код, чтобы `TestSearch` класса. Код переопределяет `SearchOptionsEnum` метод, который обеспечивает реализацию поиска определить, является ли данный параметр или отключить. Код в `SearchOptionsEnum` добавляет параметр, чтобы учитывать регистр для <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> перечислителя. Параметр, чтобы учитывать регистр также доступны в качестве `MatchCaseOption` свойство.  
  
    ```csharp  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
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
  
2.  В `TestSearchTask` класса, раскомментируйте следующие строки в `OnStartSearch` метод:  
  
    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```
  
3.  Проверьте параметр:  
  
    1.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
    2.  В окне инструментов, выберите стрелку вниз справа от текстового поля.  
  
         **Учитывать регистр** отображается флажок.  
  
    3.  Выберите **учитывать регистр** флажок, а затем выполнить некоторые запросы поиска.  
  
## <a name="to-add-a-search-filter"></a>Чтобы добавить фильтр поиска  
 Можно добавить фильтры поиска, которые позволяют пользователям уточнить набор целевых объектов поиска. Например можно выполнить фильтрацию файлов в проводнике, даты, на которых они были последнего изменения и расширениях имен файлов. В этом пошаговом руководстве вы добавите фильтр даже только для строк. При выборе этого фильтра, узел поиска добавляет строки, указываемые в запросе поиска. Можно определить эти строки внутри метода поиска и фильтрации целевых объектов поиска соответствующим образом.  
  
1.  В *TestSearch.cs* добавьте следующий код, чтобы `TestSearch` класса. Этот код реализует `SearchFiltersEnum` , добавив <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> , указывающий для фильтрации результатов поиска так, чтобы отображались только четные строки.  
  
    ```csharp  
    public override IVsEnumWindowSearchFilters SearchFiltersEnum  
    {  
        get  
        {  
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();  
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));  
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;  
        }  
    }  
  
    ```  
  
     Теперь элемент управления поиска отображает фильтр поиска `Search even lines only`. Когда пользователь выбирает фильтр, строка `lines:"even"` отображается в поле поиска. Другие критерии поиска могут отображаться в то же время в качестве фильтра. Строки поиска могут предшествовать фильтра, после фильтра, или оба.  
  
2.  В *TestSearch.cs* добавьте следующие методы для `TestSearchTask` класс, который находится в `TestSearch` класса. Эти методы поддерживают `OnStartSearch` метод, который необходимо изменить на следующем шаге.  
  
    ```csharp  
    private string RemoveFromString(string origString, string stringToRemove)  
    {  
        int index = origString.IndexOf(stringToRemove);  
        if (index == -1)  
            return origString;  
        else   
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();  
    }  
  
    private string[] GetEvenItems(string[] contentArr)  
    {  
        int length = contentArr.Length / 2;  
        string[] evenContentArr = new string[length];  
  
        int indexB = 0;  
        for (int index = 1; index < contentArr.Length; index += 2)  
        {  
            evenContentArr[indexB] = contentArr[index];  
            indexB++;  
        }  
  
        return evenContentArr;  
    }  
    ```  
  
3.  В `TestSearchTask` классе `OnStartSearch` метод следующим кодом. Это изменение обновляет код для поддержки фильтра.  
  
    ```csharp  
    protected override void OnStartSearch()  
    {  
        // Use the original content of the text box as the target of the search.   
        var separator = new string[] { Environment.NewLine };  
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
  
5.  Выполните сборку решения и запустите отладку. В экспериментальном экземпляре Visual Studio откройте окно инструментов и затем нажмите кнопку со стрелкой вниз на элементе управления поиска.  
  
     **Учитывать регистр** флажок и **искать только даже строки** фильтра отображаются.  
  
6.  Выберите нужный фильтр.  
  
     Содержит поле поиска **строк: «четными»**, и отображаются следующие результаты:  
  
     Хороший 2  
  
     4 good  
  
     6 goodbye  
  
7.  Удалить `lines:"even"` из поля поиска, выберите **учитывать регистр** флажок, а затем введите `g` в поле поиска.  
  
     Отображаются следующие результаты:  
  
     Переход 1  
  
     Хороший 2  
  
     5 goodbye  
  
8.  Нажмите кнопку X справа от поля поиска.  
  
     Поиска очищается и отображается исходное содержимое. Тем не менее **учитывать регистр** по-прежнему установлен флажок.