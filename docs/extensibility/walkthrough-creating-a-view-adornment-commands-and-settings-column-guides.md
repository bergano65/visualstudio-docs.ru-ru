---
title: "Создание оформления представления, команды и параметры | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
caps.latest.revision: 7
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
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: f37f2f8243a49f4f85b0f4177f2f33a7a724f08b
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-a-view-adornment-commands-and-settings-column-guides"></a>Пошаговое руководство: Создание оформления представления, команд и параметров (направляющие столбцов)
Можно расширить редактор текста или кода Visual Studio с командами и Просмотр эффектов.  В этом разделе показано, как приступить к работе с компонентом популярные расширения направляющие столбцов.  Направляющие столбцов являются визуально света линий, нарисованных для представления текстового редактора для управления код, чтобы ширина определенных столбцов.  Специально форматированные кода может быть важно примеры включают в документах, в блогах, или отчеты об ошибках.  
  
 В этом пошаговом руководстве вы научитесь:  
  
-   Создайте проект VSIX  
  
-   Добавьте элемент оформления представление редактора  
  
-   Добавление поддержки для сохранения и получения параметров (там, где для рисования направляющие столбцов и их цвет)  
  
-   Добавьте команды (Добавление и удаление столбцов, изменения их цвета)  
  
-   Поместите команды в меню "Правка" и текста документа контекстные меню  
  
-   Добавление поддержки для вызова команд из окна команд Visual Studio  
  
 Вы можете проверить версию направляющим столбец с этой коллекции Visual Studio[расширение](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home).  
  
 **Примечание**: в этом пошаговом руководстве вставке большого объема кода в несколько файлов, созданных шаблонами расширения visual studio, но скоро в этом пошаговом руководстве будет ссылаться на готовое решение на github с другими примерами расширения.  Полный код немного отличается тем, что значки реальные команды вместо использования generictemplate значки.  
  
## <a name="getting-started"></a>Начало работы  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="setting-up-the-solution"></a>Настройка решения  
 Сначала будет создайте проект VSIX, добавьте элемент оформления представление редактора и затем добавить команду (который добавляет VSPackage владельцем команды).  Базовая архитектура выглядит следующим образом:  
  
-   У вас есть прослушиватель создания представления текста, который создает `ColumnGuideAdornment` объекта на представление.  Этот объект прослушивает события об изменении представления или изменение параметров, обновление или перерисовка столбец руководства по необходимости.  
  
-   Существует `GuidesSettingsManager` , выполняет чтение и запись из хранилища параметров Visual Studio.  Диспетчер параметров также имеет операции для обновления параметров, поддерживаемых команд user (Добавить столбец, удалить столбец, измените цвет).  
  
-   Существует пакет VSIP, который необходим, если у вас есть команды пользователя, но это просто стандартный код, который инициализирует объект реализации команд.  
  
-   Существует `ColumnGuideCommands` объекта, реализующего команды пользователя и подключает обработчиков команд для команд, объявленных в файле .vsct.  
  
 **VSIX**.  Используйте **файл | Новые функции...** Команда для создания проекта.  Выберите узел расширения в C# в левой области навигации и щелкните **проект VSIX** в правой области.  Введите имя ColumnGuides и выберите **ОК** для создания проекта.  
  
 **Просмотр оформления**.  Нажмите правой кнопкой мыши узел проекта в обозревателе решений.  Выберите **добавить | Новый элемент...** Команда для добавления нового элемента представления обрамления.  Выберите **расширяемости | Редактор** в левой области навигации и выберите **обрамления просмотра редактора** в правой области.  Введите имя ColumnGuideAdornment в качестве имени элемента и выберите **добавить** Чтобы добавить его.  
  
 Можно увидеть этот шаблон элемента добавлено два файла проекта (а также ссылки и так далее): ColumnGuideAdornment.cs и ColumnGuideAdornmentTextViewCreationListener.cs.  Шаблоны только прямоугольник фиолетовый на представление.  Ниже будет изменить на несколько строк в прослушивателе создания представления и замените содержимое файла ColumnGuideAdornment.cs.  
  
 **Команды**.  Нажмите правой кнопкой мыши узел проекта в обозревателе решений.  Выберите **добавить | Новый элемент...** Команда для добавления нового элемента представления обрамления.  Выберите **расширяемости | VSPackage** в левой области навигации и выберите **настраиваемой команды** в правой области.  Введите имя ColumnGuideCommands в качестве имени элемента и выберите **добавить** Чтобы добавить его.  Помимо несколько ссылок Добавление команд и пакета добавлены ColumnGuideCommands.cs, ColumnGuideCommandsPackage.cs и ColumnGuideCommandsPackage.vsct.  Ниже заменит содержимое первого и последнего файлов для определения и реализации этих команд.  
  
## <a name="setting-up-the-text-view-creation-listener"></a>Настройка прослушивателя создания представления текста  
 Откройте ColumnGuideAdornmentTextViewCreationListener.cs в редакторе.  Этот код реализует обработчик для всякий раз, когда Visual Studio создает текстового представления.  Существуют атрибуты, определяющие, когда обработчик вызывается в зависимости от характеристик представления.  
  
 Код также необходимо объявить слой оформлений.  Когда редактор обновляет представления, он получает слои оформления для представления и из того, что возвращает элементы оформления.  Можно объявить упорядочение уровень по отношению к другим с атрибутами.  Замените следующую строку:  
  
```c#  
[Order(After = PredefinedAdornmentLayers.Caret)]  
```  
  
 с помощью этих двух строк:  
  
```c#  
[Order(Before = PredefinedAdornmentLayers.Text)]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
```  
  
 В группе атрибуты, объявляющие слой оформлений — строку, которую Вы заменили.   Первая строка изменяются только изменения, где отображаются направляющих столбцов.  Рисование линий «до» текст в представлении означает, что они отображаются за или под текстом.  Во второй строке объявляет оформлений руководство столбца применимы к сущности текста, соответствующие вашей понятие документа, что может объявлять оформления, например, для работы только для редактирования текста.  Дополнительные сведения в [языковой службы и точек расширения редактора](../extensibility/language-service-and-editor-extension-points.md)  
  
## <a name="implementing-the-settings-manager"></a>Реализация диспетчера параметров  
 Замените содержимое GuidesSettingsManager.cs следующий код (как описано ниже):  
  
```c#  
using Microsoft.VisualStudio.Settings;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.Shell.Settings;  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Windows.Media;  
  
namespace ColumnGuides  
{  
    internal static class GuidesSettingsManager  
    {  
        // Because my code is always called from the UI thred, this succeeds.  
        internal static SettingsManager VsManagedSettingsManager =  
            new ShellSettingsManager(ServiceProvider.GlobalProvider);  
  
        private const int _maxGuides = 5;  
        private const string _collectionSettingsName = "Text Editor";  
        private const string _settingName = "Guides";  
        // 1000 seems reasonable since primary scenario is long lines of code  
        private const int _maxColumn = 1000;   
  
        static internal bool AddGuideline(int column)  
        {  
            if (! IsValidColumn(column))  
                throw new ArgumentOutOfRangeException(  
                    "column",  
                    "The paramenter must be between 1 and " + _maxGuides.ToString());  
            var offsets = GuidesSettingsManager.GetColumnOffsets();  
            if (offsets.Count() >= _maxGuides)  
                return false;  
            // Check for duplicates  
            if (offsets.Contains(column))  
                return false;  
            offsets.Add(column);  
            WriteSettings(GuidesSettingsManager.GuidelinesColor, offsets);  
            return true;  
        }  
  
        static internal bool RemoveGuideline(int column)  
        {  
            if (!IsValidColumn(column))  
                throw new ArgumentOutOfRangeException(  
                    "column", "The paramenter must be between 1 and 10,000");  
            var columns = GuidesSettingsManager.GetColumnOffsets();  
            if (! columns.Remove(column))  
            {  
                // Not present.  Allow user to remove the last column   
                // even if they're not on the right column.  
                if (columns.Count != 1)  
                    return false;  
  
                columns.Clear();  
            }  
            WriteSettings(GuidesSettingsManager.GuidelinesColor, columns);  
            return true;  
        }  
  
        static internal bool CanAddGuideline(int column)  
        {  
            if (!IsValidColumn(column))  
                return false;  
            var offsets = GetColumnOffsets();  
            if (offsets.Count >= _maxGuides)  
                return false;  
            return ! offsets.Contains(column);  
        }  
  
        static internal bool CanRemoveGuideline(int column)  
        {  
            if (! IsValidColumn(column))  
                return false;  
            // Allow user to remove the last guideline regardless of the column.  
            // Okay to call count, we limit the number of guides.  
            var offsets = GuidesSettingsManager.GetColumnOffsets();  
            return offsets.Contains(column) || offsets.Count() == 1;  
        }  
  
        static internal void RemoveAllGuidelines()  
        {  
            WriteSettings(GuidesSettingsManager.GuidelinesColor, new int[0]);  
        }  
  
        private static bool IsValidColumn(int column)  
        {  
            // zero is allowed (per user request)  
            return 0 <= column && column <= _maxColumn;  
        }  
  
        // This has format "RGB(<int>, <int>, <int>) <int> <int>...".  
        // There can be any number of ints following the RGB part,   
        // and each int is a column (char offset into line) where to draw.  
        static private string _guidelinesConfiguration;  
        static private string GuidelinesConfiguration  
        {  
            get  
            {  
                if (_guidelinesConfiguration == null)  
                {  
                    _guidelinesConfiguration =   
                        GetUserSettingsString(  
                            GuidesSettingsManager._collectionSettingsName,  
                            GuidesSettingsManager._settingName)  
                        .Trim();  
                }  
                return _guidelinesConfiguration;  
            }  
  
            set  
            {  
                if (value != _guidelinesConfiguration)  
                {  
                    _guidelinesConfiguration = value;  
                    WriteUserSettingsString(  
                        GuidesSettingsManager._collectionSettingsName,  
                        GuidesSettingsManager._settingName, value);  
                    // Notify ColumnGuideAdornments to update adornments in views.  
                    var handler = GuidesSettingsManager.SettingsChanged;  
                    if (handler != null)  
                        handler();  
                }  
            }  
        }  
  
        internal static string GetUserSettingsString(string collection, string setting)  
        {  
            var store = GuidesSettingsManager  
                            .VsManagedSettingsManager  
                            .GetReadOnlySettingsStore(SettingsScope.UserSettings);  
            return store.GetString(collection, setting, "RGB(255,0,0) 80");  
        }  
  
        internal static void WriteUserSettingsString(string key, string propertyName,  
                                                     string value)  
        {  
            var store = GuidesSettingsManager  
                            .VsManagedSettingsManager  
                            .GetWritableSettingsStore(SettingsScope.UserSettings);  
            store.CreateCollection(key);  
            store.SetString(key, propertyName, value);  
        }  
  
        // Persists settings and sets property with side effect of signaling  
        // ColumnGuideAdornments to update.  
        static private void WriteSettings(Color color, IEnumerable<int> columns)  
        {  
            string value = ComposeSettingsString(color, columns);  
            GuidelinesConfiguration = value;  
        }  
  
        private static string ComposeSettingsString(Color color,  
                                                    IEnumerable<int> columns)  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.AppendFormat("RGB({0},{1},{2})", color.R, color.G, color.B);  
            IEnumerator<int> columnsEnumerator = columns.GetEnumerator();  
            if (columnsEnumerator.MoveNext())  
            {  
                sb.AppendFormat(" {0}", columnsEnumerator.Current);  
                while (columnsEnumerator.MoveNext())  
                {  
                    sb.AppendFormat(", {0}", columnsEnumerator.Current);  
                }  
            }  
            return sb.ToString();  
        }  
  
        // Parse a color out of a string that begins like "RGB(255,0,0)"  
        static internal Color GuidelinesColor  
        {  
            get  
            {  
                string config = GuidelinesConfiguration;  
                if (!String.IsNullOrEmpty(config) && config.StartsWith("RGB("))  
                {  
                    int lastParen = config.IndexOf(')');  
                    if (lastParen > 4)  
                    {  
                        string[] rgbs = config.Substring(4, lastParen - 4).Split(',');  
  
                        if (rgbs.Length >= 3)  
                        {  
                            byte r, g, b;  
                            if (byte.TryParse(rgbs[0], out r) &&  
                                byte.TryParse(rgbs[1], out g) &&  
                                byte.TryParse(rgbs[2], out b))  
                            {  
                                return Color.FromRgb(r, g, b);  
                            }  
                        }  
                    }  
                }  
                return Colors.DarkRed;  
            }  
  
            set  
            {  
                WriteSettings(value, GetColumnOffsets());  
            }  
        }  
  
        // Parse a list of integer values out of a string that looks like  
        // "RGB(255,0,0) 1, 5, 10, 80"  
        static internal List<int> GetColumnOffsets()  
        {  
            var result = new List<int>();  
            string settings = GuidesSettingsManager.GuidelinesConfiguration;  
            if (String.IsNullOrEmpty(settings))  
                return new List<int>();  
  
            if (!settings.StartsWith("RGB("))  
                return new List<int>();  
  
            int lastParen = settings.IndexOf(')');  
            if (lastParen <= 4)  
                return new List<int>();  
  
            string[] columns = settings.Substring(lastParen + 1).Split(',');  
  
            int columnCount = 0;  
            foreach (string columnText in columns)  
            {  
                int column = -1;  
                // VS 2008 gallery extension didn't allow zero, so per user request ...  
                if (int.TryParse(columnText, out column) && column >= 0)  
                {  
                    columnCount++;  
                    result.Add(column);  
                    if (columnCount >= _maxGuides)  
                        break;  
                }  
            }  
            return result;  
        }  
  
        // Delegate and Event to fire when settings change so that ColumnGuideAdornments   
        // can update.  We need nothing special in this event since the settings manager   
        // is statically available.  
        //  
        internal delegate void SettingsChangedHandler();  
        static internal event SettingsChangedHandler SettingsChanged;  
  
    }  
}  
  
```  
  
 Большая часть кода просто создает и выполняет синтаксический анализ формата параметров: «RGB (\<int настроек,\<int настроек,\<int настроек) \<int настроек, \<int настроек,...».  Целые числа в конце — это столбцы с единицы, место направляющие столбцов.  Расширение направляющие столбцов захватывает все параметры в строке значение одного параметра.  
  
 Существуют некоторые части кода, которую следует обратить внимание.  Следующий код возвращает управляемую оболочку Visual Studio для хранения параметров.  В большинстве случаев это абстрагирует через реестр Windows, но этот API не зависит от механизма хранения.  
  
```c#  
internal static SettingsManager VsManagedSettingsManager =  
    new ShellSettingsManager(ServiceProvider.GlobalProvider);  
```  
  
 Хранение параметров Visual Studio использует идентификатор категории и значение идентификатора для уникальной идентификации всех параметров:  
  
```c#  
private const string _collectionSettingsName = "Text Editor";  
private const string _settingName = "Guides";  
```  
  
 Необходимо использовать `“Text Editor”` категорию имя и можно выбрать любое название.  
  
 Первые несколько функции являются точками входа для изменения параметров.  Они проверять ограничения высокого уровня, как максимальное количество направляющие разрешены.  Затем они вызвать `WriteSettings` которого составляет строку параметров и задает свойство `GuideLinesConfiguration`.  Это свойство сохраняет значение параметров Visual Studio параметры хранилища и инициирует `SettingsChanged` событий для обновления всех `ColumnGuideAdornment` объектов, каждый из которых связан с помощью текстового представления.  
  
 Существует несколько функций точки входа, такие как `CanAddGuideline`, которые используются для реализации команд, позволяющих изменить параметры.  Когда Visual Studio отображается меню, он запрашивает реализации команд, чтобы увидеть, если команда включена, именем и т. д.  Ниже показано, как подключить эти точки входа для реализации команд.  В разделе [расширение меню и команд](../extensibility/extending-menus-and-commands.md) Дополнительные сведения о командах.  
  
## <a name="implementing-the-columnguideadornment-class"></a>Реализация класса ColumnGuideAdornment  
 `ColumnGuideAdornment` Класса создается для каждого представления текста, могут иметь элементы оформления.  Это класс прослушивает события об изменении представления или изменение параметров, обновление или перерисовка столбец руководства по необходимости.  
  
 Замените содержимое ColumnGuideAdornment.cs следующий код (как описано ниже):  
  
```c#  
using System;  
using System.Windows.Media;  
using Microsoft.VisualStudio.Text.Editor;  
using System.Collections.Generic;  
using System.Windows.Shapes;  
using Microsoft.VisualStudio.Text.Formatting;  
using System.Windows;  
  
namespace ColumnGuides  
{  
    /// <summary>  
    /// Adornment class, one instance per text view that draws a guides on the viewport  
    /// </summary>  
    internal sealed class ColumnGuideAdornment  
    {  
        private const double _lineThickness = 1.0;  
        private IList<Line> _guidelines;  
        private IWpfTextView _view;  
        private double _baseIndentation;  
        private double _columnWidth;  
  
        /// <summary>  
        /// Creates editor column guidelines  
        /// </summary>  
        /// <param name="view">The <see cref="IWpfTextView"/> upon   
        /// which the adornment will be drawn</param>  
        public ColumnGuideAdornment(IWpfTextView view)  
        {  
            _view = view;  
            _guidelines = CreateGuidelines();  
            GuidesSettingsManager.SettingsChanged +=   
                new GuidesSettingsManager.SettingsChangedHandler(SettingsChanged);  
            view.LayoutChanged +=   
                new EventHandler<TextViewLayoutChangedEventArgs>(OnViewLayoutChanged);  
            _view.Closed += new EventHandler(OnViewClosed);  
        }  
  
        void SettingsChanged()  
        {  
            _guidelines = CreateGuidelines();  
            UpdatePositions();  
            AddGuidelinesToAdornmentLayer();  
        }  
  
        void OnViewClosed(object sender, EventArgs e)  
        {  
            _view.LayoutChanged -= OnViewLayoutChanged;  
            _view.Closed -= OnViewClosed;  
            GuidesSettingsManager.SettingsChanged -= SettingsChanged;  
        }  
  
        private bool _firstLayoutDone;  
  
        void OnViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
        {  
            bool fUpdatePositions = false;  
  
            IFormattedLineSource lineSource = _view.FormattedLineSource;  
            if (lineSource == null)  
            {  
                return;  
            }  
            if (_columnWidth != lineSource.ColumnWidth)  
            {  
                _columnWidth = lineSource.ColumnWidth;  
                fUpdatePositions = true;  
            }  
            if (_baseIndentation != lineSource.BaseIndentation)  
            {  
                _baseIndentation = lineSource.BaseIndentation;  
                fUpdatePositions = true;  
            }  
            if (fUpdatePositions ||  
                e.VerticalTranslation ||  
                e.NewViewState.ViewportTop != e.OldViewState.ViewportTop ||  
                e.NewViewState.ViewportBottom != e.OldViewState.ViewportBottom)  
            {  
                UpdatePositions();  
            }  
            if (!_firstLayoutDone)  
            {  
                AddGuidelinesToAdornmentLayer();  
                _firstLayoutDone = true;  
            }  
        }  
  
        private static IList<Line> CreateGuidelines()  
        {  
            Brush lineBrush = new SolidColorBrush(GuidesSettingsManager.GuidelinesColor);  
            DoubleCollection dashArray = new DoubleCollection(new double[] { 1.0, 3.0 });  
            IList<Line> result = new List<Line>();  
            foreach (int column in GuidesSettingsManager.GetColumnOffsets())  
            {  
                Line line = new Line()  
                {  
                    // Use the DataContext slot as a cookie to hold the column  
                    DataContext = column,  
                    Stroke = lineBrush,  
                    StrokeThickness = _lineThickness,  
                    StrokeDashArray = dashArray  
                };  
                result.Add(line);  
            }  
            return result;  
        }  
  
        void UpdatePositions()  
        {  
            foreach (Line line in _guidelines)  
            {  
                int column = (int)line.DataContext;  
                line.X2 = _baseIndentation + 0.5 + column * _columnWidth;  
                line.X1 = line.X2;  
                line.Y1 = _view.ViewportTop;  
                line.Y2 = _view.ViewportBottom;  
            }  
        }  
  
        void AddGuidelinesToAdornmentLayer()  
        {  
            // Grab a reference to the adornment layer that this adornment   
            // should be added to  
            // Must match exported name in ColumnGuideAdornmentTextViewCreationListener  
            IAdornmentLayer adornmentLayer =   
                _view.GetAdornmentLayer("ColumnGuideAdornment");  
            if (adornmentLayer == null)  
                return;  
            adornmentLayer.RemoveAllAdornments();  
            // Add the guidelines to the adornment layer and make them relative   
            // to the viewport  
            foreach (UIElement element in _guidelines)  
                adornmentLayer.AddAdornment(AdornmentPositioningBehavior.OwnerControlled,  
                                            null, null, element, null);  
        }  
    }  
  
}  
```  
  
 Экземпляры этого класса удерживать связанного <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>и список `Line` объектов, рисуемых в представлении.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>  
  
 Конструктор (вызывается из `ColumnGuideAdornmentTextViewCreationListener` когда Visual Studio создает новые представления) создает направляющая столбца `Line` объектов.  Конструктор также добавляет обработчики для `SettingsChanged` событий (определенные в `GuidesSettingsManager`) и Просмотр событий `LayoutChanged` и `Closed`.  
  
 `LayoutChanged` Вызывает событие из-за несколько видов изменений в представлении, в том числе Visual Studio создаст представление.  `OnViewLayoutChanged` Обработчик вызывает функцию `AddGuidelinesToAdornmentLayer` для выполнения.  Код в `OnViewLayoutChanged` определяет, должен ли он для обновления строки позиций, основываясь на изменения, такие как изменения размера шрифта, представление переплета, горизонтальной прокрутки и т. д.  Код в `UpdatePositions` вызывает направляющих для рисования между символами или сразу после колонки текста, смещение указанного символа в строке текста.  
  
 При каждом изменении параметров `SettingsChanged` функция просто заново создает все `Line` объекты с любые новые параметры.  После задания позиции строки, код удаляет все предыдущие `Line` объектов из `ColumnGuideAdornment` слой оформления и добавляет новые шаблоны.  
  
## <a name="defining-the-commands-menus-and-menu-placements"></a>Определение команд, меню и размещения меню  
 Может существовать намного объявление меню и команд, размещения на другие меню группы команд или меню и подключение обработчиков команд.  В этом пошаговом руководстве представлены работу команды этого расширения, но более сведения см. в разделе [расширение меню и команд](../extensibility/extending-menus-and-commands.md).  
  
### <a name="introduction-to-the-code"></a>Введение в код  
 Расширение направляющие столбцов показано объявление группы команд, которые связаны друг с другом (Добавить столбец, удалить столбец, измените цвет линии) и затем помещение этой группы в подменю контекстного меню редактора.  Расширение направляющие столбцов также добавляет команды в главном **изменить** меню но поддерживает для них невидимыми, рассматривается как общий шаблон ниже.  
  
 Реализация команд, состоит из трех частей: ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage.vsct и ColumnGuideCommands.cs.  Код, созданный с использованием шаблонов помещает команду **средства** меню, которое выводит диалоговое окно с реализацией.  Можно просмотреть, реализации в файлах ColumnGuideCommands.cs и .vsct, поскольку это довольно просто.  Код в этих файлах ниже будет заменено.  
  
 Код пакета является стандартным объявления, которые необходимы для Visual Studio, чтобы обнаружить, что модуль предоставляет команды и поместить команды.  При инициализации пакета, создать экземпляр класса реализации команд.  См. Дополнительные сведения о пакетах, относящиеся к командам, расположенную выше команды.  
  
### <a name="a-common-commands-pattern"></a>Общий шаблон команд  
 Команды в модуле направляющие столбцов являются примером очень распространенный шаблон в Visual Studio.  Поместите связанных команд в группу, и поместить эту группу в главном меню выберите часто с «`<CommandFlag>CommandWellOnly</CommandFlag>`» установите, чтобы команда невидимым.  Размещение команд в главном меню (таких как **изменить**) таким образом дает им имена с низким приоритетом (такие как **Edit.AddColumnGuide**) которые полезны для поиска команд при переназначении привязок клавиш в **Сервис Параметры** и получения завершения при вызове команды из **окно командной строки**.  
  
 Затем добавьте группы команд в контекстных меню или вложенные меню, где предполагается, что пользователь для использования команд.  Visual Studio обрабатывает `CommandWellOnly` как с флагом видимости для главных меню только.  При размещении той же группе команд в контекстное меню или подменю, команды являются видимыми.  
  
 В составе общий шаблон расширения направляющие столбцов создается вторая группа, содержащая один подменю.  Меню «sub» в свою очередь содержит первую группу с помощью команд руководство по четыре столбца.  Вторая группа, содержащая подменю является многократно используемые актив, поместить на различные контекстные меню, который помещает эти контекстные меню подменю.  
  
### <a name="the-vsct-file"></a>Файл .vsct  
 В файле .vsct объявляется команды и где переходят, а также значки и т. д.  Замените содержимое файла .vsct (как описано ниже) следующий код:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
  <!--  This is the file that defines the actual layout and type of the commands.  
        It is divided in different sections (e.g. command definition, command  
        placement, ...), with each defining a specific set of properties.  
        See the comment before each section for more details about how to  
        use it. -->  
  
  <!--  The VSCT compiler (the tool that translates this file into the binary  
        format that VisualStudio will consume) has the ability to run a preprocessor  
        on the vsct file; this preprocessor is (usually) the C++ preprocessor, so  
        it is possible to define includes and macros with the same syntax used  
        in C++ files. Using this ability of the compiler here, we include some files  
        defining some of the constants that we will use inside the file. -->  
  
  <!--This is the file that defines the IDs for all the commands exposed by   
      VisualStudio. -->  
  <Extern href="stdidcmd.h"/>  
  
  <!--This header contains the command ids for the menus provided by the shell. -->  
  <Extern href="vsshlids.h"/>  
  
  <!--The Commands section is where commands, menus, and menu groups are defined.  
      This section uses a Guid to identify the package that provides the command   
      defined inside it. -->  
  <Commands package="guidColumnGuideCommandsPkg">  
    <!-- Inside this section we have different sub-sections: one for the menus, another    
    for the menu groups, one for the buttons (the actual commands), one for the combos   
    and the last one for the bitmaps used. Each element is identified by a command id  
    that is a unique pair of guid and numeric identifier; the guid part of the identifier  
    is usually called "command set" and is used to group different command inside a  
    logically related group; your package should define its own command set in order to  
    avoid collisions with command ids defined by other packages. -->  
  
    <!-- In this section you can define new menu groups. A menu group is a container for   
         other menus or buttons (commands); from a visual point of view you can see the   
         group as the part of a menu contained between two lines. The parent of a group   
         must be a menu. -->  
    <Groups>  
  
      <!-- The main group is parented to the edit menu. All the buttons within the group  
           have the "CommandWellOnly" flag, so they're actually invisible, but it means  
           they get canonical names that begin with "Edit". Using placements, the group  
           is also placed in the GuidesSubMenu group. -->  
      <!-- The priority 0xB801 is chosen so it goes just after   
           IDG_VS_EDIT_COMMANDWELL -->  
      <Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
      <!-- Group for holding the "Guidelines" sub-menu anchor (the item on the menu that  
           drops the sub menu). The group is parented to  
           the context menu for code windows. That takes care of most editors, but it's  
           also placed in a couple of other windows using Placements -->  
      <Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_CODEWIN" />  
      </Group>  
  
    </Groups>  
  
    <Menus>  
      <Menu guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" priority="0x1000"  
            type="Menu">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup" />  
        <Strings>  
          <ButtonText>&Column Guides</ButtonText>  
        </Strings>  
      </Menu>  
    </Menus>  
  
    <!--Buttons section. -->  
    <!--This section defines the elements the user can interact with, like a menu command or a button   
        or combo box in a toolbar. -->  
    <Buttons>  
      <!--To define a menu group you have to specify its ID, the parent menu and its   
          display priority.   
          The command is visible and enabled by default. If you need to change the   
          visibility, status, etc, you can use the CommandFlag node.  
          You can add more than one CommandFlag node e.g.:  
              <CommandFlag>DefaultInvisible</CommandFlag>  
              <CommandFlag>DynamicVisibility</CommandFlag>  
          If you do not want an image next to your command, remove the Icon node or   
          set it to <Icon guid="guidOfficeIcon" id="msotcidNoIcon" /> -->  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
              priority="0x0100" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <Icon guid="guidImages" id="bmpPicAddGuide" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <CommandFlag>AllowParams</CommandFlag>  
        <Strings>  
          <ButtonText>&Add Column Guide</ButtonText>  
        </Strings>  
      </Button>  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveColumnGuide"   
              priority="0x0101" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <Icon guid="guidImages" id="bmpPicRemoveGuide" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <CommandFlag>AllowParams</CommandFlag>  
        <Strings>  
          <ButtonText>&Remove Column Guide</ButtonText>  
        </Strings>  
      </Button>  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidChooseGuideColor"   
              priority="0x0103" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <Icon guid="guidImages" id="bmpPicChooseColor" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <Strings>  
          <ButtonText>Column Guide &Color...</ButtonText>  
        </Strings>  
      </Button>  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveAllColumnGuides"   
              priority="0x0102" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <Strings>  
          <ButtonText>Remove A&ll Columns</ButtonText>  
        </Strings>  
      </Button>  
    </Buttons>  
  
    <!--The bitmaps section is used to define the bitmaps that are used for the  
        commands.-->  
    <Bitmaps>  
      <!--  The bitmap id is defined in a way that is a little bit different from the  
            others:   
            the declaration starts with a guid for the bitmap strip, then there is the  
            resource id of the bitmap strip containing the bitmaps and then there are   
            the numeric ids of the elements used inside a button definition. An important  
            aspect of this declaration is that the element id   
            must be the actual index (1-based) of the bitmap inside the bitmap strip. -->  
      <Bitmap guid="guidImages" href="Resources\ColumnGuideCommands.png"   
              usedList="bmpPicAddGuide, bmpPicRemoveGuide, bmpPicChooseColor" />  
    </Bitmaps>  
  
  </Commands>  
  
  <CommandPlacements>  
  
    <!-- Define secondary placements for our groups -->  
  
    <!-- Place the group containing the three commands in the sub-menu -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                      priority="0x0100">  
      <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
    </CommandPlacement>  
  
    <!-- The HTML editor context menu, for some reason, redefines its own groups  
         so we need to place a copy of our context menu there too. -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_HTML" />  
    </CommandPlacement>  
  
    <!-- The HTML context menu in Dev12 changed. -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp_Dev12" id="IDMX_HTM_SOURCE_HTML_Dev12" />  
    </CommandPlacement>  
  
    <!-- Similarly for Script -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"  
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_SCRIPT" />  
    </CommandPlacement>  
  
    <!-- Similarly for ASPX  -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_ASPX" />  
    </CommandPlacement>  
  
    <!-- Similarly for the XAML editor context menu -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"  
                      priority="0x0600">  
      <Parent guid="guidXamlUiCmds" id="IDM_XAML_EDITOR" />  
    </CommandPlacement>  
  
  </CommandPlacements>  
  
  <!-- This defines the identifiers and their values used above to index resources  
       and specify commands. -->  
  <Symbols>  
    <!-- This is the package guid. -->  
    <GuidSymbol name="guidColumnGuideCommandsPkg"   
                value="{e914e5de-0851-4904-b361-1a3a9d449704}" />  
  
    <!-- This is the guid used to group the menu commands together -->  
    <GuidSymbol name="guidColumnGuidesCommandSet"   
                value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
      <IDSymbol name="GuidesContextMenuGroup" value="0x1020" />  
      <IDSymbol name="GuidesMenuItemsGroup" value="0x1021" />  
      <IDSymbol name="GuidesSubMenu" value="0x1022" />  
      <IDSymbol name="cmdidAddColumnGuide" value="0x0100" />  
      <IDSymbol name="cmdidRemoveColumnGuide" value="0x0101" />  
      <IDSymbol name="cmdidChooseGuideColor" value="0x0102" />  
      <IDSymbol name="cmdidRemoveAllColumnGuides" value="0x0103" />  
    </GuidSymbol>  
  
    <GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
      <IDSymbol name="bmpPicAddGuide" value="1" />  
      <IDSymbol name="bmpPicRemoveGuide" value="2" />  
      <IDSymbol name="bmpPicChooseColor" value="3" />  
    </GuidSymbol>  
  
    <GuidSymbol name="CMDSETID_HtmEdGrp_Dev12"   
                value="{78F03954-2FB8-4087-8CE7-59D71710B3BB}">  
      <IDSymbol name="IDMX_HTM_SOURCE_HTML_Dev12" value="0x1" />  
    </GuidSymbol>  
  
    <GuidSymbol name="CMDSETID_HtmEdGrp" value="{d7e8c5e1-bdb8-11d0-9c88-0000f8040a53}">  
      <IDSymbol name="IDMX_HTM_SOURCE_HTML" value="0x33" />  
      <IDSymbol name="IDMX_HTM_SOURCE_SCRIPT" value="0x34" />  
      <IDSymbol name="IDMX_HTM_SOURCE_ASPX" value="0x35" />  
    </GuidSymbol>  
  
    <GuidSymbol name="guidXamlUiCmds" value="{4c87b692-1202-46aa-b64c-ef01faec53da}">  
      <IDSymbol name="IDM_XAML_EDITOR" value="0x103" />  
    </GuidSymbol>  
  </Symbols>  
  
</CommandTable>  
  
```  
  
 **ИДЕНТИФИКАТОРЫ GUID**.  Visual Studio можно найти обработчики команд и вызвать их необходимо убедиться, что пакет GUID, объявленного в файле ColumnGuideCommandsPackage.cs (создается на основе шаблона элемента проекта) соответствует пакета GUID, объявленного в файле .vsct (скопированный ранее).  При повторном использовании этого образца кода, следует убедиться, что у вас есть свой идентификатор GUID, чтобы вы не конфликтовали с любого, кто может скопировать этот код.  
  
 Найдите следующую строку в ColumnGuideCommandsPackage.cs и скопируйте GUID от кавычки:  
  
```c#  
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";  
```  
  
 Вставьте идентификатор GUID в файле .vsct, чтобы получить следующую строку вашей `Symbols` объявления:  
  
```xml  
<GuidSymbol name="guidColumnGuideCommandsPkg"   
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />  
```  
  
 Значение GUID для команды и растровый рисунок слишком должно быть уникальным для расширений:  
  
```xml  
<GuidSymbol name="guidColumnGuidesCommandSet"   
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
```  
  
 Тем не менее не нужно изменять набор команд и растровые изображения GUID в этом пошаговом руководстве для получения кода для работы.  Идентификатор GUID, должна соответствовать объявление в файле ColumnGuideCommands.cs набор команд, но содержимое этого файла будет заменено слишком; Таким образом будет соответствовать идентификаторы GUID.  
  
 Другие идентификаторы GUID в файле .vsct определить существующие меню, к которым добавляются команды руководство столбца, поэтому они никогда не изменится.  
  
 **Разделы файла**.  .vsct состоит из трех разделов внешнего: команд, размещения и символы.  В разделе команд определяет группы команд, меню, кнопки и пункты меню и растровых изображений для значков.  В разделе Размещение объявляется, куда групп в меню и дополнительных размещения на существующих меню.  В разделе символы объявляется идентификаторы, используемые в других местах файла .vsct, которая делает более удобочитаемыми, чем GUID и шестнадцатеричные числа везде кода .vsct.  
  
 **Команды раздела, группирует определения**.  В разделе команд сначала определяет группы команд.  Группа команд являются команды в меню с незначительные серые линии разделения групп.  Группа также может заполнить весь подменю, как показано в этом примере и не отображается серым цветом, в этом случае Разделение строк.  Vsct-файлах объявляет две группы `GuidesMenuItemsGroup` , является родительским по отношению к `IDM_VS_MENU_EDIT` (главный **изменить** меню) и `GuidesContextMenuGroup` , является родительским по отношению к `IDM_VS_CTXT_CODEWIN` (контекстное меню редактора кода).  
  
 Вторая группа объявление содержит `0x0600` приоритет:  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
```  
  
 Идея состоит в поместить столбец проводит подменю в конце любого контекстного меню, к которому мы добавляем группе вложенного меню.  Тем не менее, не следует думать, лучше знать и принудительно подменю всегда быть последней с помощью приоритет `0xFFFF`.  Необходимо поэкспериментировать с этим номером, чтобы увидеть, где находится ваш подменю на контекстные меню, куда поместить.  В этом случае `0x0600` достаточно велико, чтобы поместить его в конце меню, как мы видим, но оставляет место для разработки расширений имен должна быть меньше расширения направляющие столбцов, если это нежелательно человеком.  
  
 **Команды в разделе определения меню**.  Далее в разделе команд определяется подменю `GuidesSubMenu`, порождены в `GuidesContextMenuGroup`.  `GuidesContextMenuGroup` — Это группа, мы добавим все соответствующие контекстные меню.  В разделе Размещение код помещает группы с помощью команд руководство по четыре столбца этого вложенного меню.  
  
 **Команды раздела, определения кнопок**.  В разделе команд определяет элементы меню или кнопок, которые имеют четыре столбца проводит команды.  `CommandWellOnly`, описанных выше, значит, команды являются невидимыми, помещенный в главном меню.  Два пункта меню кнопку объявлений (добавьте руководство и удалить руководство) также имеют `AllowParams` флага:  
  
```xml  
<CommandFlag>AllowParams</CommandFlag>  
```  
  
 Этот флаг позволяет, наряду с наличие размещения главного меню, команду, чтобы получить аргументы, когда Visual Studio вызывает обработчик команды.  Если пользователь вызывает команду из окна команд, возвращает передан аргумент обработчика событий аргументов.  
  
 **Команды разделов, точечные рисунки определения**.  Наконец в разделе команды объявляется точечные рисунки и значки, используемый для команд.  Это простое объявление, которое определяет ресурс проекта и перечисляет индексы на основе один из значков, используемых.  В разделе "символы" файла .vsct объявляет значения идентификаторов, использовать в качестве индексов.  В этом пошаговом руководстве используется панель изображений, предоставленных с шаблоном элемента пользовательской команды добавлен в проект.  
  
 **Раздел размещения**.  После команды раздел является разделом размещения.  Первый из них —, где код добавляет первой группы, описанных выше, содержит четыре столбца руководство команды вложенного меню расположения команды:  
  
```xml  
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                  priority="0x0100">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
</CommandPlacement>  
```  
  
 Добавьте все другие размещения `GuidesContextMenuGroup` (который содержит `GuidesSubMenu`) на другие контекстные меню редактора.  При объявлении код `GuidesContextMenuGroup`, он был родительским по отношению к контекстное меню редактора кода.  Вот почему вы не видите размещения для контекстного меню редактора кода.  
  
 **Символы раздел**.  Как уже говорилось выше, в разделе символы объявляется идентификаторы, используемые в других местах файла .vsct, которая делает более удобочитаемыми, чем GUID и шестнадцатеричные числа везде кода .vsct.  Важные места в этом разделе, что идентификатор GUID пакета должен соответствовать объявление в классе пакета и набор команд, GUID должны согласиться с помощью объявления в классе реализации команды.  
  
## <a name="implementing-the-commands"></a>Реализация команды  
 Файл ColumnGuideCommands.cs реализует команды и подключает обработчиков.  Когда Visual Studio загружает пакет и инициализирует его, в свою очередь вызывает пакет `Initialize` на класс реализации команд.  Команды инициализации просто создает экземпляр класса, и конструктор подключает всех обработчиков команд.  
  
 Замените содержимое файла ColumnGuideCommands.cs (как описано ниже) следующий код:  
  
```c#  
using System;  
using System.ComponentModel.Design;  
using System.Globalization;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.Shell.Interop;  
using Microsoft.VisualStudio.TextManager.Interop;  
using Microsoft.VisualStudio.Text.Editor;  
using Microsoft.VisualStudio;  
  
namespace ColumnGuides  
{  
    /// <summary>  
    /// Command handler  
    /// </summary>  
    internal sealed class ColumnGuideCommands  
    {  
  
        const int cmdidAddColumnGuide = 0x0100;  
        const int cmdidRemoveColumnGuide = 0x0101;  
        const int cmdidChooseGuideColor = 0x0102;  
        const int cmdidRemoveAllColumnGuides = 0x0103;  
  
        /// <summary>  
        /// Command menu group (command set GUID).  
        /// </summary>  
        static readonly Guid CommandSet =   
            new Guid("c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e");  
  
        /// <summary>  
        /// VS Package that provides this command, not null.  
        /// </summary>  
        private readonly Package package;  
  
        OleMenuCommand _addGuidelineCommand;  
        OleMenuCommand _removeGuidelineCommand;  
  
        /// <summary>  
        /// Initializes the singleton instance of the command.  
        /// </summary>  
        /// <param name="package">Owner package, not null.</param>  
        public static void Initialize(Package package)  
        {  
            Instance = new ColumnGuideCommands(package);  
        }  
  
        /// <summary>  
        /// Gets the instance of the command.  
        /// </summary>  
        public static ColumnGuideCommands Instance  
        {  
            get;  
            private set;  
        }  
  
        /// <summary>  
        /// Initializes a new instance of the <see cref="ColumnGuideCommands"/> class.  
        /// Adds our command handlers for menu (commands must exist in the command   
        /// table file)  
        /// </summary>  
        /// <param name="package">Owner package, not null.</param>  
        private ColumnGuideCommands(Package package)  
        {  
            if (package == null)  
            {  
                throw new ArgumentNullException("package");  
            }  
  
            this.package = package;  
  
            // Add our command handlers for menu (commands must exist in the .vsct file)  
  
            OleMenuCommandService commandService =  
                this.ServiceProvider.GetService(typeof(IMenuCommandService))  
                    as OleMenuCommandService;  
            if (commandService != null)  
            {  
                // Add guide  
                _addGuidelineCommand =   
                    new OleMenuCommand(AddColumnGuideExecuted, null,  
                                       AddColumnGuideBeforeQueryStatus,  
                                       new CommandID(ColumnGuideCommands.CommandSet,  
                                                     cmdidAddColumnGuide));  
                _addGuidelineCommand.ParametersDescription = "<column>";  
                commandService.AddCommand(_addGuidelineCommand);  
                // Remove guide  
                _removeGuidelineCommand =  
                    new OleMenuCommand(RemoveColumnGuideExecuted, null,  
                                       RemoveColumnGuideBeforeQueryStatus,  
                                       new CommandID(ColumnGuideCommands.CommandSet,  
                                                     cmdidRemoveColumnGuide));  
                _removeGuidelineCommand.ParametersDescription = "<column>";  
                commandService.AddCommand(_removeGuidelineCommand);  
                // Choose color  
                commandService.AddCommand(  
                    new MenuCommand(ChooseGuideColorExecuted,  
                                    new CommandID(ColumnGuideCommands.CommandSet,  
                                                  cmdidChooseGuideColor)));  
                // Remove all  
                commandService.AddCommand(  
                    new MenuCommand(RemoveAllGuidelinesExecuted,  
                                    new CommandID(ColumnGuideCommands.CommandSet,  
                                                  cmdidRemoveAllColumnGuides)));  
            }  
        }  
  
        /// <summary>  
        /// Gets the service provider from the owner package.  
        /// </summary>  
        private IServiceProvider ServiceProvider  
        {  
            get  
            {  
                return this.package;  
            }  
        }  
  
        private void AddColumnGuideBeforeQueryStatus(object sender, EventArgs e)  
        {  
            int currentColumn = GetCurrentEditorColumn();  
            _addGuidelineCommand.Enabled =  
                GuidesSettingsManager.CanAddGuideline(currentColumn);  
        }  
  
        private void RemoveColumnGuideBeforeQueryStatus(object sender, EventArgs e)  
        {  
            int currentColumn = GetCurrentEditorColumn();  
            _removeGuidelineCommand.Enabled =  
                GuidesSettingsManager.CanRemoveGuideline(currentColumn);  
        }  
  
        private int GetCurrentEditorColumn()  
        {  
            IVsTextView view = GetActiveTextView();  
            if (view == null)  
            {  
                return -1;  
            }  
  
            try  
            {  
                IWpfTextView textView = GetTextViewFromVsTextView(view);  
                int column = GetCaretColumn(textView);  
  
                // Note: GetCaretColumn returns 0-based positions. Guidelines are 1-based  
                // positions.  
                // However, do not subtract one here since the caret is positioned to the  
                // left of  
                // the given column and the guidelines are positioned to the right. We  
                // want the  
                // guideline to line up with the current caret position. e.g. When the  
                // caret is  
                // at position 1 (zero-based), the status bar says column 2. We want to  
                // add a  
                // guideline for column 1 since that will place the guideline where the  
                // caret is.  
                return column;  
            }  
            catch (InvalidOperationException)  
            {  
                return -1;  
            }  
        }  
  
        /// <summary>  
        /// Find the active text view (if any) in the active document.  
        /// </summary>  
        /// <returns>The IVsTextView of the active view, or null if there is no active  
        /// document or the  
        /// active view in the active document is not a text view.</returns>  
        private IVsTextView GetActiveTextView()  
        {  
            IVsMonitorSelection selection =  
                this.ServiceProvider.GetService(typeof(IVsMonitorSelection))  
                                                    as IVsMonitorSelection;  
            object frameObj = null;  
            ErrorHandler.ThrowOnFailure(  
                selection.GetCurrentElementValue(  
                    (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame, out frameObj));  
  
            IVsWindowFrame frame = frameObj as IVsWindowFrame;  
            if (frame == null)  
            {  
                return null;  
            }  
  
            return GetActiveView(frame);  
        }  
  
        private static IVsTextView GetActiveView(IVsWindowFrame windowFrame)  
        {  
            if (windowFrame == null)  
            {  
                throw new ArgumentException("windowFrame");  
            }  
  
            object pvar;  
            ErrorHandler.ThrowOnFailure(  
                windowFrame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView, out pvar));  
  
            IVsTextView textView = pvar as IVsTextView;  
            if (textView == null)  
            {  
                IVsCodeWindow codeWin = pvar as IVsCodeWindow;  
                if (codeWin != null)  
                {  
                    ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));  
                }  
            }  
            return textView;  
        }  
  
        private static IWpfTextView GetTextViewFromVsTextView(IVsTextView view)  
        {  
  
            if (view == null)  
            {  
                throw new ArgumentNullException("view");  
            }  
  
            IVsUserData userData = view as IVsUserData;  
            if (userData == null)  
            {  
                throw new InvalidOperationException();  
            }  
  
            object objTextViewHost;  
            if (VSConstants.S_OK  
                   != userData.GetData(Microsoft.VisualStudio  
                                                .Editor  
                                                .DefGuidList.guidIWpfTextViewHost,  
                                       out objTextViewHost))  
            {  
                throw new InvalidOperationException();  
            }  
  
            IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;  
            if (textViewHost == null)  
            {  
                throw new InvalidOperationException();  
            }  
  
            return textViewHost.TextView;  
        }  
  
        /// <summary>  
        /// Given an IWpfTextView, find the position of the caret and report its column  
        /// number. The column number is 0-based  
        /// </summary>  
        /// <param name="textView">The text view containing the caret</param>  
        /// <returns>The column number of the caret's position. When the caret is at the  
        /// leftmost column, the return value is zero.</returns>  
        private static int GetCaretColumn(IWpfTextView textView)  
        {  
            // This is the code the editor uses to populate the status bar.  
            Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =  
                textView.Caret.ContainingTextViewLine;  
            double columnWidth = textView.FormattedLineSource.ColumnWidth;  
            return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)  
                                       / columnWidth));  
        }  
  
        /// <summary>  
        /// Determine the applicable column number for an add or remove command.  
        /// The column is parsed from command arguments, if present. Otherwise  
        /// the current position of the caret is used to determine the column.  
        /// </summary>  
        /// <param name="e">Event args passed to the command handler.</param>  
        /// <returns>The column number. May be negative to indicate the column number is  
        /// unavailable.</returns>  
        /// <exception cref="ArgumentException">The column number parsed from event args  
        /// was not a valid integer.</exception>  
        private int GetApplicableColumn(EventArgs e)  
        {  
            var inValue = ((OleMenuCmdEventArgs)e).InValue as string;  
            if (!string.IsNullOrEmpty(inValue))  
            {  
                int column;  
                if (!int.TryParse(inValue, out column) || column < 0)  
                    throw new ArgumentException("Invalid column");  
                return column;  
            }  
  
            return GetCurrentEditorColumn();  
        }  
  
        /// <summary>  
        /// This function is the callback used to execute a command when the a menu item  
        /// is clicked. See the Initialize method to see how the menu item is associated  
        /// to this function using the OleMenuCommandService service and the MenuCommand  
        /// class.  
        /// </summary>  
        private void AddColumnGuideExecuted(object sender, EventArgs e)  
        {  
            int column = GetApplicableColumn(e);  
            if (column >= 0)  
            {  
                GuidesSettingsManager.AddGuideline(column);  
            }  
        }  
  
        private void RemoveColumnGuideExecuted(object sender, EventArgs e)  
        {  
            int column = GetApplicableColumn(e);  
            if (column >= 0)  
            {  
                GuidesSettingsManager.RemoveGuideline(column);  
            }  
        }  
  
        private void RemoveAllGuidelinesExecuted(object sender, EventArgs e)  
        {  
            GuidesSettingsManager.RemoveAllGuidelines();  
        }  
  
        private void ChooseGuideColorExecuted(object sender, EventArgs e)  
        {  
            System.Windows.Media.Color color = GuidesSettingsManager.GuidelinesColor;  
  
            using (System.Windows.Forms.ColorDialog picker =   
                new System.Windows.Forms.ColorDialog())  
            {  
                picker.Color = System.Drawing.Color.FromArgb(255, color.R, color.G,  
                                                             color.B);  
                if (picker.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
                {  
                    GuidesSettingsManager.GuidelinesColor =   
                        System.Windows.Media.Color.FromRgb(picker.Color.R,  
                                                           picker.Color.G,   
                                                           picker.Color.B);  
                }  
            }  
        }  
  
    }  
}  
  
```  
  
 **Исправлены ссылки**.  Отсутствует ссылка на этом этапе.  Нажмите правой кнопкой мыши на узел ссылки в обозревателе решений.  Выберите **добавить...** команда.  **Добавить ссылку** диалогового окна есть поле поиска в правом верхнем углу.  Введите «редактор» (без кавычек).  Выберите **Microsoft.VisualStudio.Editor** элемента (необходимо проверить поле слева от элемента, не просто выберите элемент) и выберите **ОК** следует добавить ссылку.  
  
 **Инициализация**.  При инициализации класса пакета, он вызывает `Initialize` на класс реализации команд.  `ColumnGuideCommands` Инициализации создает экземпляр класса и сохраняет экземпляр класса и ссылки на пакет в членах класса.  
  
 Давайте рассмотрим один обработчик ИБП обработчик команды из конструктора класса:  
  
```c#  
_addGuidelineCommand =   
    new OleMenuCommand(AddColumnGuideExecuted, null,  
                       AddColumnGuideBeforeQueryStatus,  
                       new CommandID(ColumnGuideCommands.CommandSet,  
                                     cmdidAddColumnGuide));  
  
```  
  
 Можно создать `OleMenuCommand`.  Visual Studio использует команды системы Microsoft Office.  Основные аргументы при создании экземпляра OleMenuCommand — функция, которая реализует команду (`AddColumnGuideExecuted`), функция, вызываемая при Visual Studio отображается меню с командой (`AddColumnGuideBeforeQueryStatus`) и идентификатор команды.  Visual studio вызывает функцию запроса состояния перед отображением команды меню, чтобы команды могли принимать сам невидимым или недоступны для выбора для отображения меню (например, отключение **копирования** Если не выбрано), изменять его значок или даже изменить его имя (например, добавить что-либо удалить что-нибудь) и так далее.  Идентификатор команды должен соответствовать идентификатор команды, объявленных в файле .vsct.  Набор строк для команды и направляющие столбцов добавьте команды и должны совпадать файла .vsct ColumnGuideCommands.cs.  
  
 Следующая строка предоставляет помощь для пользователей вызвать команду через окно команд (как описано ниже):  
  
```c#  
_addGuidelineCommand.ParametersDescription = "<column>";  
```  
  
 **Запрос состояния**.  Функции состояния запроса `AddColumnGuideBeforeQueryStatus` и `RemoveColumnGuideBeforeQueryStatus` проверить некоторые параметры (например, максимальное число направляющие или столбца, max) или если направляющая столбца для удаления.  Они позволяют команды, если условиям.  Функции состояния запроса должны быть очень эффективным, так как они выполняются каждый раз, когда Visual Studio отображается меню, для каждой команды в меню.  
  
 **Функция AddColumnGuideExecuted**.  Интересная часть Добавление руководство является выяснение текущее представление редактора расположение курсора.  Во-первых, эта функция вызывает `GetApplicableColumn` проверяющего, если существует заданным пользователем аргументом в аргументах событий обработчик команды, и если такового не имеется, функция проверяет представление редактора:  
  
```c#  
private int GetApplicableColumn(EventArgs e)  
{  
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;  
    if (!string.IsNullOrEmpty(inValue))  
    {  
        int column;  
        if (!int.TryParse(inValue, out column) || column < 0)  
            throw new ArgumentException("Invalid column");  
        return column;  
    }  
  
    return GetCurrentEditorColumn();  
}  
  
```  
  
 `GetCurrentEditorColumn`имеет с продуктом для верного <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>представления кода.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>  Если производится трассировка через `GetActiveTextView`, `GetActiveView`, и `GetTextViewFromVsTextView`, можно увидеть, как это сделать.  Ниже приведен соответствующий код абстрагируется, начиная с текущего выделения, затем получение кадр начало DocView кадров как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, затем получение <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>из IVsTextView получения просмотра узла и, наконец, IWpfTextView:</xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
```c#  
   IVsMonitorSelection selection =  
       this.ServiceProvider.GetService(typeof(IVsMonitorSelection))   
           as IVsMonitorSelection;  
   object frameObj = null;  
  
ErrorHandler.ThrowOnFailure(selection.GetCurrentElementValue(  
                                (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame,  
                                out frameObj));  
  
   IVsWindowFrame frame = frameObj as IVsWindowFrame;  
   if (frame == null)  
       <<do nothing>>;  
  
...  
   object pvar;  
   ErrorHandler.ThrowOnFailure(frame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView,  
                                                  out pvar));  
  
   IVsTextView textView = pvar as IVsTextView;  
   if (textView == null)  
   {  
       IVsCodeWindow codeWin = pvar as IVsCodeWindow;  
       if (codeWin != null)  
       {  
           ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));  
       }  
   }  
  
...  
   if (textView == null)  
       <<do nothing>>  
  
   IVsUserData userData = textView as IVsUserData;  
   if (userData == null)  
       <<do nothing>>  
  
   object objTextViewHost;  
   if (VSConstants.S_OK   
           != userData.GetData(Microsoft.VisualStudio.Editor.DefGuidList  
                                                            .guidIWpfTextViewHost,  
                                out objTextViewHost))  
   {  
       <<do nothing>>  
   }  
  
   IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;  
   if (textViewHost == null)  
       <<do nothing>>  
  
   IWpfTextView textView = textViewHost.TextView;  
  
```  
  
 После IWpfTextView, вы можете получить столбец, где находится курсор:  
  
```c#  
private static int GetCaretColumn(IWpfTextView textView)  
{  
    // This is the code the editor uses to populate the status bar.  
    Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =  
        textView.Caret.ContainingTextViewLine;  
    double columnWidth = textView.FormattedLineSource.ColumnWidth;  
    return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)  
                                / columnWidth));  
}  
  
```  
  
 В текущем столбце руку там, где пользователь щелкнул, код просто вызывает в диспетчере параметров для добавления или удаления столбца.  Диспетчер параметров запускает событие, в котором все `ColumnGuideAdornment` объекты прослушивания.  При возникновении события, эти объекты обновить их представления связанный текст с помощью новых параметров столбца руководства.  
  
## <a name="invoking-command-from-the-command-window"></a>Вызов команд из окна команд  
 Образец направляющие столбцов позволяет пользователям вызывать две команды в командном окне как форма расширяемости.  Если вы используете **View | Другие окна | Командное окно** команды можно увидеть в командном окне.  Можно взаимодействовать с командное окно, введя «изменить» и завершения имя команды и указав аргумент 120, у вас есть следующее:  
  
```  
> Edit.AddColumnGuide 120  
>  
```  
  
 Части образца, которые представлены в объявлениях файла .vsct, включить `ColumnGuideCommands` конструктор класса, когда оно подключается реализации обработчика команды, проверьте аргументы события и обработчики команд.  
  
 Вы уже видели»`<CommandFlag>CommandWellOnly</CommandFlag>`» в файл .vsct, а также размещения в главном меню Правка хотя мы больше не показывать команды в **изменить** меню пользовательского интерфейса.  Они имеются в главном меню Правка дает им имена, такие как **Edit.AddColumnGuide**.  Команды в группе объявление, которое содержит четыре команды помещаться группы меню Правка напрямую.  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
```  
  
 Раздел кнопок Далее объявлены команды `CommandWellOnly` для обеспечения их невидимым в главном меню и их с объявленным `AllowParams`:  
  
```xml  
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
        priority="0x0100" type="Button">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
  <Icon guid="guidImages" id="bmpPicAddGuide" />  
  <CommandFlag>CommandWellOnly</CommandFlag>  
  <CommandFlag>AllowParams</CommandFlag>  
  
```  
  
 Вы уже видели подключить код в обработчик команд `ColumnGuideCommands` конструктор класса представленное описание допустимых параметров:  
  
```c#  
_addGuidelineCommand.ParametersDescription = "<column>";  
  
```  
  
 Вы уже видели `GetApplicableColumn` функции проверки `OleMenuCmdEventArgs` для значения перед проверкой представление редактора для текущего столбца:  
  
```c#  
private int GetApplicableColumn(EventArgs e)  
{  
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;  
    if (!string.IsNullOrEmpty(inValue))  
    {  
        int column;  
        if (!int.TryParse(inValue, out column) || column < 0)  
            throw new ArgumentException("Invalid column");  
        return column;  
    }  
  
```  
  
## <a name="trying-your-extension"></a>Попытка расширения  
 Теперь можно нажать клавишу **F5** выполнить расширение направляющие столбцов.  Откройте текстовый файл и используйте контекстное меню редактора Добавление направляющих, удалять и изменять их цвет.  Необходимо выбрать в текст (пробелы не прошел конец строки) для добавления столбца руководство или редактор добавляет его в последний столбец в строке.  Если использовать командную строку и вызывать команды с аргументом, можно добавить в любом направляющие столбцов.  
  
 Если вы хотите попробовать другой команде размещения, изменить имена, значки и т. д и наличии проблем с отображением последнюю кода в меню Visual Studio, можно сбросить экспериментальный куст вы отладку.  Открыть **меню «Пуск» Windows** и введите «reset».  Найти и вызвать команду **Сброс Далее экспериментального экземпляра Visual Studio**.  Это приведет к очистке экспериментальный куст всех компонентов расширения.  Нет очистки, параметры из компонентов, таким образом все руководства бы при завершении работы Visual Studio экспериментальный куст останется код считывает хранилища параметров при следующем запуске.  
  
## <a name="finished-code-project"></a>Готовый код проекта  
 Скоро будет проект github примеры расширяемости Visual Studio, а там будет весь проект.  В этом разделе для указания существует в этом случае будет обновлена.  Завершенный образец проекта могут иметь разные идентификаторы GUID и будет иметь панелью различными растровыми изображениями для значки команд.  
  
 Вы можете проверить версию направляющим столбец с этой коллекции Visual Studio[расширение](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home).  
  
## <a name="see-also"></a>См. также  
 [В редакторе](../extensibility/inside-the-editor.md)   
 [Расширение редактора и языковые службы](../extensibility/extending-the-editor-and-language-services.md)   
 [Служба языка и точек расширения редактора](../extensibility/language-service-and-editor-extension-points.md)   
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)   
 [Добавление подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md)   
 [Создание расширения с помощью редактора шаблона элемента](../extensibility/creating-an-extension-with-an-editor-item-template.md)
