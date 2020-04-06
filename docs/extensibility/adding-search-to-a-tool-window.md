---
title: Добавление поиска в окно инструмента (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9112a3368ba604c4291f9018e763022e953c4fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740147"
---
# <a name="add-search-to-a-tool-window"></a>Добавление поиска в окно инструмента
При создании или обновлении окна инструмента в расширении можно добавить ту же функциональность поиска, которая появляется в других местах visual Studio. Эта функциональность включает в себя следующие функции:

- Окно поиска, которое всегда находится в пользовательской области панели инструментов.

- Индикатор прогресса, наложенный на сам ящик поиска.

- Возможность показывать результаты, как только вы вводите каждый символ (мгновенный поиск) или только после того, как вы выберете ключ **Enter** (поиск по запросу).

- Список, в котором указаны термины, по которым вы искали совсем недавно.

- Возможность фильтрации поиска по определенным полям или аспектам целей поиска.

Следуя этому пошаговому шагу, вы узнаете, как выполнять следующие задачи:

1. Создайте проект VSPackage.

2. Создайте окно инструментов, содержащее UserControl с текстовым материалом только для чтения.

3. Добавьте окно поиска в окно инструмента.

4. Добавьте реализацию поиска.

5. Включить мгновенный поиск и отображение панели прогресса.

6. Добавьте опцию **«Матч-кейс».**

7. Добавить **поиск ровные строки только** фильтр.

## <a name="to-create-a-vsix-project"></a>Создание проекта VSIX

1. Создайте проект VSIX под названием `TestToolWindowSearch` с помощью окна инструмента под названием **TestSearch.** Если вам нужна помощь в этом, [см. Создание расширения с окном инструмента.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="to-create-a-tool-window"></a>Создание окна инструмента

1. В `TestToolWindowSearch` проекте откройте файл *TestSearchControl.xaml.*

2. Замените `<StackPanel>` существующий блок следующим блоком, который <xref:System.Windows.Controls.TextBox> добавляет <xref:System.Windows.Controls.UserControl> только для чтения окно инструмента.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. В *TestSearchControl.xaml.cs* файле добавьте следующую директиву с помощью:

    ```csharp
    using System.Text;
    ```

4. Удалите `button1_Click()` метод.

     В классе **TestSearchControl** добавьте следующий код.

     Этот код добавляет <xref:System.Windows.Controls.TextBox> публичное свойство под названием **SearchResultsTextBox** и общедоступное свойство строки под названием **SearchContent**. В конструкторе SearchResultsTextBox устанавливается в текстовое поле, а SearchContent инициализирован к новому набору строк. Содержимое текстового поля также инициализировано к набору строк.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Выполните сборку решения и запустите отладку. Появляется экспериментальный экземпляр Visual Studio.

6. В панели меню выберите **Посмотреть** > другие**Тест-поиск****Windows.** > 

     Окно инструмента отображается, но управление поиска еще не отображается.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Добавление окна поиска в окно инструмента

1. В *TestSearch.cs* файле добавьте в `TestSearch` класс следующий код. Код переопределяет <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> свойство, так что `true`получить доступ возвращается.

     Чтобы включить поиск, необходимо <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> переопределить свойство. Класс <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> и предоставляет реализацию по умолчанию, которая не позволяет осуществлять поиск.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Выполните сборку решения и запустите отладку. Появляется экспериментальный экземпляр.

3. В экспериментальном экземпляре Visual Studio, открыть **TestSearch**.

     В верхней части окна инструмента отображается контроль поиска с водяным знаком **Поиска** и значком с увеличительным стеклом. Однако поиск пока не работает, так как процесс поиска не реализован.

## <a name="to-add-the-search-implementation"></a>Добавление реализации поиска
 При включании <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>поиска на , как и в предыдущей процедуре, окно инструмента создает хост поиска. Этот узла настраивает и управляет процессами поиска, которые всегда происходят на фоновом потоке. Поскольку <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> класс управляет созданием хоста поиска и настройкой поиска, необходимо только создать задачу поиска и предоставить метод поиска. Процесс поиска происходит на фоновом потоке, а вызовы в управление окнами инструмента происходят в потоке uI. Поэтому для управления любыми вызовами, которые вы делаете при работе с управлением, необходимо использовать метод [ThreadHelper.Invoke.](https://msdn.microsoft.com/data/ee197798(v=vs.85))

1. В *TestSearch.cs* файле добавьте следующие `using` директивы:

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

2. В `TestSearch` классе добавьте следующий код, который выполняет следующие действия:

    - Переопределяет <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> метод создания задачи поиска.

    - Переопределяет <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> метод восстановления состояния текстового поля. Этот метод вызывается, когда пользователь отменяет задачу поиска и когда пользователь устанавливает или отменяет параметры или фильтры. Оба <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> и вызваны на потоке uI. Таким образом, вам не нужно получать доступ к текстовому ящику с помощью метода [ThreadHelper.Invoke.](https://msdn.microsoft.com/data/ee197798(v=vs.85))

    - Создает класс, который `TestSearchTask` называется, <xref:Microsoft.VisualStudio.Shell.VsSearchTask>который наследует от <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>, который обеспечивает реализацию по умолчанию.

         В `TestSearchTask`, конструктор устанавливает частное поле, которое ссылается на окно инструмента. Чтобы предоставить метод поиска, <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> вы <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> переопределить и методы. Метод <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> — это метод, в котором выполняется процесс поиска. Этот процесс включает в себя выполнение поиска, отображение результатов поиска в текстовом поле и вызов реализации базового класса этого метода, чтобы сообщить, что поиск завершен.

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

3. Проверьте реализацию поиска, выполнив следующие действия:

    1. Перестроить проект и начать отладку.

    2. В экспериментальном экземпляре Visual Studio снова откройте окно инструмента, введите текст поиска в окне поиска и нажмите **ENTER**.

         Должны появиться правильные результаты.

## <a name="to-customize-the-search-behavior"></a>Настройка поведения поиска
 Изменяя настройки поиска, можно внести различные изменения в то, как отображается элемент управления поиска и как выполняется поиск. Например, можно изменить водяной знак (текст по умолчанию, который отображается в поле поиска), минимальную и максимальную ширину управления поиском, а также отображать панель прогресса. Вы также можете изменить точку, в которой начинают отображаться результаты поиска (по требованию или мгновенному поиску) и показывать ли список терминов, по которым вы недавно искали. Вы можете найти полный список <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> настроек в классе.

1. В файле TestSearch.cs» добавьте следующий `TestSearch` код в класс. Этот код позволяет мгновенный поиск, а не по требованию поиска (имеется в виду, что пользователь не должен нажать **ENTER**). Код переопределяет `ProvideSearchSettings` метод в `TestSearch` классе, что необходимо для изменения настроек по умолчанию.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Проверьте новую настройку, перестроив решение и перезапустив отладчик.

     Результаты поиска отображаются каждый раз, когда вы вводите символ в поле поиска.

3. В `ProvideSearchSettings` методе добавьте следующую строку, которая позволяет отображать панель прогресса.

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

     Для того чтобы отображается бар хода, необходимо сообщить о ходе работы. Чтобы сообщить о ходе работы, `OnStartSearch` не `TestSearchTask` прокомментируйте следующий код в методе класса:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. Чтобы замедлить обработку достаточно, чтобы панель прогресса была `OnStartSearch` видна, `TestSearchTask` не комментируйте следующую строку в методе класса:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Проверьте новые настройки, перестроив решение и начав отладку.

     Панель прогресса отображается в окне поиска (как синяя строка ниже текстового окна поиска) каждый раз, когда вы выполняете поиск.

## <a name="to-enable-users-to-refine-their-searches"></a>Для уточнения поиска пользователями
 Вы можете разрешить пользователям совершенствовать свои поиски с помощью таких опций, как **матч случае** или матч **всего слова**. Варианты могут быть boolean, которые появляются как флажки, или команды, которые отображаются как кнопки. Для этого пошагового, вы создадите вариант boolean.

1. В *TestSearch.cs* файле добавьте в `TestSearch` класс следующий код. Код переопределяет `SearchOptionsEnum` метод, который позволяет реализации поиска определить, является ли данный вариант в выключенном состоянии или выключен. Код добавляет `SearchOptionsEnum` опцию, сопоминая корпусу <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> с регистратором. Опция для соответствия случае также `MatchCaseOption` предоставляется в качестве свойства.

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

2. В `TestSearchTask` классе не комментируйте следующую `OnStartSearch` строку в методе:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Проверьте опцию:

    1. Выполните сборку решения и запустите отладку. Появляется экспериментальный экземпляр.

    2. В окне инструмента выберите стрелку Down на правой стороне текстового окна.

         Появляется флажок **для случая матча.**

    3. Выберите флажок **для случая матча,** а затем выполните некоторые поиски.

## <a name="to-add-a-search-filter"></a>Добавление фильтра поиска
 Можно добавить фильтры поиска, которые позволяют пользователям усовершенствовать набор целей поиска. Например, можно отфильтровать файлы в File Explorer по датам, в которые они были изменены совсем недавно, и расширениям их имени. В этом пошаговом слове вы добавите фильтр только для линий. Когда пользователь выбирает этот фильтр, хост поиска добавляет строки, указанные в поисковом запросе. Затем можно определить эти строки в методе поиска и соответствующим образом отфильтровать цели поиска.

1. В *TestSearch.cs* файле добавьте в `TestSearch` класс следующий код. Код реализуется `SearchFiltersEnum` путем <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> добавления, который определяет для фильтрации результатов поиска, так что только даже строки появляются.

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

     Теперь управление поиском отображает `Search even lines only`фильтр поиска. Когда пользователь выбирает фильтр, строка `lines:"even"` появляется в поле поиска. Другие критерии поиска могут отображаться одновременно с фильтром. Строки поиска могут отображаться до фильтра, после фильтра или и того, и другого.

2. В *TestSearch.cs* файла добавьте следующие `TestSearchTask` методы в `TestSearch` класс, который находится в классе. Эти методы `OnStartSearch` поддерживают метод, который вы измените на следующем этапе.

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

3. В `TestSearchTask` классе обновите `OnStartSearch` метод следующим кодом. Это изменение обновляет код для поддержки фильтра.

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

4. Проверьте свой код.

5. Выполните сборку решения и запустите отладку. В экспериментальном экземпляре Visual Studio откройте окно инструмента, а затем выберите стрелку Down на элементе поиска.

     Коробка проверки **случая матча** и линии **поиска ровные линии только** отображаются.

6. Выберите фильтр.

     Коробка поиска содержит **строки:"даже"**, и следующие результаты появляются:

     2 хороших

     4 Хорошо

     6 Прощай

7. Удалить `lines:"even"` из окна поиска, выберите флажок `g` **случая матча,** а затем введите в поле поиска.

     Появляются следующие результаты:

     1 идти

     2 хороших

     5 до свидания

8. Выберите X на правой стороне окна поиска.

     Поиск очищается, и отображается исходное содержимое. Тем не менее, флажок **случая матча** все еще выбран.
