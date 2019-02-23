---
title: Создание оформления представления, команд и параметров | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd5bfc24fcf1cd8a465bafe1e5bcf6c4df61308c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722295"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>Пошаговое руководство. Создание оформления представления, команд и параметров (направляющие столбцов)
Вы можете расширить редактор текста или кода Visual Studio с командами и эффектов представления. В этой статье показано, как приступить к работе с компонентом популярное расширение, направляющие столбцов. Направляющие столбцов являются визуально света линий, рисуемых в представлении текстового редактора, чтобы помочь в управлении код, чтобы ширина определенных столбцов. В частности форматированный код может быть важно для примеры включают в документах, в блогах, или отчеты об ошибках.

В этом пошаговом руководстве вы:
- Создайте проект VSIX
- Добавьте элемент оформления представления редактора
- Добавление поддержки для сохранения и знакомство с параметрами (там, где их цвет и draw направляющие столбцов)
- Добавление команд (Добавить или удалить направляющие столбцов, изменения их цвета)
- Поместите команду в меню "Правка" и текст документа контекстные меню
- Добавить поддержку для вызова команд из командного окна Visual Studio

  Вы можете опробовать версию функции направляющие столбец с данной коллекцией Visual Studio[расширение](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines).

  **Примечание**. В этом пошаговом руководстве вставьте значительную кода в несколько файлов, создаваемых Шаблоны расширения Visual Studio. Но вскоре в этом пошаговом руководстве будет ссылаться на полноценное решение на GitHub с другими примерами расширения. Полный код несколько отличается, у нее есть значки реальные команды вместо использования generictemplate значки.

## <a name="get-started"></a>Начало работы
Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Этот пакет включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="set-up-the-solution"></a>Настройка решения
Во-первых создайте проект VSIX, добавьте элемент оформления представления редактора и затем добавить команду (который добавляет VSPackage, которая будет владеть команды). Базовая архитектура выглядит следующим образом:
- У вас есть прослушиватель создания представления текста, который создает `ColumnGuideAdornment` объекта в каждом представлении. Этот объект прослушивает события об изменении представления или параметры изменение, обновления или обновить столбец руководства по мере необходимости.
- Существует `GuidesSettingsManager` , выполняет чтение и запись из хранилища параметров Visual Studio. Диспетчер параметров также имеет операции для обновления параметров, которые поддерживают пользовательские команды (Добавление столбца, удалить столбец, измените цвет).
- Имеется пакет VSIP, который является обязательным, если у вас есть команды пользователя, но это просто стандартный код, который инициализирует объект реализации команд.
- Существует `ColumnGuideCommands` объект, который запускает пользователь, команды и подключает обработчик команды для команды, объявленных в *.vsct* файла.

  **VSIX**. Используйте **файл &#124; New...**  команду, чтобы создать проект. Выберите **расширяемости** узле **C#** в области навигации слева и выберите **проект VSIX** в области справа. Введите имя **ColumnGuides** и выберите **ОК** для создания проекта.

  **Просмотр оформления**. Нажмите правую кнопку указателя на узел проекта в обозревателе решений. Выберите **добавить &#124; новый элемент...**  команду, чтобы добавить новый элемент оформления представления. Выберите **расширяемости &#124; редактор** в области навигации слева и выберите **оформление окна просмотра редактора** в области справа. Введите имя **ColumnGuideAdornment** элемента укажите имя и **добавить** Чтобы добавить его.

  Вы увидите, что этот шаблон элемента добавлено два файла для проекта (а также ссылки и т. д.). **ColumnGuideAdornment.cs** и **ColumnGuideAdornmentTextViewCreationListener.cs**. Шаблоны нарисовать сиреневый прямоугольник в представление. В следующем разделе вы измените на несколько строк в представление создания прослушивателя и замените содержимое файла **ColumnGuideAdornment.cs**.

  **Команды**. В **обозревателе решений**, нажмите правую кнопку указателя на узел проекта. Выберите **добавить &#124; новый элемент...**  команду, чтобы добавить новый элемент оформления представления. Выберите **расширяемости &#124; VSPackage** в области навигации слева и выберите **настраиваемой команды** в области справа. Введите имя **ColumnGuideCommands** элемента укажите имя и **добавить**. В дополнение к несколько ссылок, добавление команд и также добавлен пакет **ColumnGuideCommands.cs**, **ColumnGuideCommandsPackage.cs**, и **ColumnGuideCommandsPackage.vsct** . В следующем разделе Замените содержимое файла первый и последний файл для определения и реализации этих команд.

## <a name="set-up-the-text-view-creation-listener"></a>Настройка прослушивателя создания представления текста
Откройте *ColumnGuideAdornmentTextViewCreationListener.cs* в редакторе. Этот код реализует обработчик для каждый раз, когда Visual Studio создает представления текста. Существуют атрибуты, определяющие, когда обработчик вызывается в зависимости от характеристик представления.

Код также необходимо объявить слое оформлений. Когда редактор представления обновлений, он получает слоев оформлений для представления и из, получает элементы оформления. Можно объявить порядок уровень по отношению к другим с атрибутами. Замените следующую строку:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

с помощью этих двух строк:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

Строки, на которой Вы заменили находится в группе атрибутов, которые объявляют слое оформлений. Первая строка вы изменили только изменения, где отображаются направляющие столбцов. Рисование линий, «до» текст в представлении означает, что они отображаются за или под текстом. Во второй строке объявляет, что элементы оформления руководство столбец применимы к текста сущностей, которые соответствуют вашей понятие документа, но вы можете объявить оформления текста, например, чтобы работает только для ввода и редактирования текста. Имеется дополнительная информация [точки расширения редактора и служба языка](../extensibility/language-service-and-editor-extension-points.md)

## <a name="implement-the-settings-manager"></a>Реализация диспетчера параметров
Замените содержимое файла *GuidesSettingsManager.cs* (как описано ниже) следующим кодом:

```csharp
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

Основная часть кода создает и выполняет синтаксический анализ формат параметров: «RGB (\<int >,\<int >,\<int >) \<int >, \<int >,...».  Целые числа в конце — это столбцы, от единицы, место направляющие столбцов. Расширение направляющие столбцов собирает все параметры в строке значение одного параметра.

Существуют некоторые части кода обратить. Следующий код возвращает управляемую оболочку Visual Studio для хранения параметров. В большинстве случаев это абстрагирует через реестр Windows, но этот API не зависит от механизма хранения.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

Параметры хранения в Visual Studio использует идентификатор категории и идентификатор параметра для уникальной идентификации все параметры:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

Нет необходимости использовать `"Text Editor"` как имя категории. Вы можете выбрать любое.

Первые несколько функции являются точками входа для изменения параметров. Они проверять ограничения высокого уровня, как максимальное число направляющие разрешено.  Затем они вызывают `WriteSettings`, который пишет строку параметров и задает свойство `GuideLinesConfiguration`. Задание этого свойства сохраняет значение параметров хранилища параметров Visual Studio и активируется `SettingsChanged` событие, чтобы обновить все `ColumnGuideAdornment` объектов, каждый из которых связан с представлением текста.

Существует несколько функций точки входа, такие как `CanAddGuideline`, которые используются для реализации команд, которые изменяют параметры. Когда Visual Studio отображается меню, он запрашивает реализации команд, чтобы увидеть, если команда включена, именем и т. д.  Ниже описано, как подключить этих точек входа для реализации команд. Дополнительные сведения о командах см. в разделе [расширить меню и команд](../extensibility/extending-menus-and-commands.md).

## <a name="implement-the-columnguideadornment-class"></a>Реализация класса ColumnGuideAdornment
`ColumnGuideAdornment` Создается экземпляр класса для каждого представления текста, который может иметь элементы оформления. Это класс прослушивает события изменения представления или параметры изменение и обновление или перерисовка направляющие столбцов при необходимости.

Замените содержимое файла *ColumnGuideAdornment.cs* (как описано ниже) следующим кодом:

```csharp
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

Экземпляры этого класса держаться связанного <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> и список `Line` объектов, нарисованных на представление.

Конструктор (вызывается из `ColumnGuideAdornmentTextViewCreationListener` когда Visual Studio создает новые представления) создается структура столбца `Line` объектов.  Конструктор также добавляет обработчики для `SettingsChanged` событий (определенные в `GuidesSettingsManager`) и события представления `LayoutChanged` и `Closed`.

`LayoutChanged` Вызывает событие из-за несколько видов изменений в представлении, в том числе Visual Studio создает представление. `OnViewLayoutChanged` Вызовов обработчика `AddGuidelinesToAdornmentLayer` для выполнения. Код в `OnViewLayoutChanged` определяет, должен ли он для обновления строки позиций, основываясь на изменения, такие как изменения размера шрифта, переплеты представление, горизонтальная прокрутка и т. д. Код в `UpdatePositions` вызывает направляющие линии для рисования между символами или сразу после колонки текста, является смещение указанного символа в строке текста.

При каждом изменении параметров, которые `SettingsChanged` функция просто заново создаст все `Line` объекты с любые новые параметры. После задания позиции строк, код удаляет все предыдущие `Line` объектов из `ColumnGuideAdornment` слое оформлений и добавляет новые.

## <a name="define-the-commands-menus-and-menu-placements"></a>Определения команд, меню и размещения меню
Может существовать намного для объявления команды и меню группы команд или меню на другие меню и размещать подключение обработчиков команд. В этом пошаговом руководстве представлены работу команды в этом расширении, но более глубокие сведения, см. в разделе [расширить меню и команд](../extensibility/extending-menus-and-commands.md).

### <a name="introduction-to-the-code"></a>Введение в код
Расширение направляющие столбцов показано объявление группы команд, которые связаны друг с другом (Добавление столбца, удалить столбец, измените цвет линии), а затем эту группу на вложенное меню из контекстном меню редактора.  Расширение направляющие столбцов также добавляет команды в главном **изменить** меню но защищает невидимым, рассматриваются как стандартная процедура ниже.

Существует реализация команд, состоит из трех частей: ColumnGuideCommandsPackage.cs ColumnGuideCommandsPackage.vsct и ColumnGuideCommands.cs. Код, созданный с помощью шаблонов помещает команду **средства** меню, которое выводит диалоговое окно с реализацией. Вы можете изучить, реализации *.vsct* и *ColumnGuideCommands.cs* файлы, так как это просто. Вы замените код в этих файлах ниже.

Код пакета содержит стандартный объявления, необходимые для Visual Studio для обнаружения, что расширение предлагает команды и чтобы найти место размещения команд. При инициализации пакета, он создает экземпляр класса реализации команд. Дополнительные сведения о пакетах, относящиеся к командам см. в разделе [расширить меню и команд](../extensibility/extending-menus-and-commands.md).

### <a name="a-common-commands-pattern"></a>Общий шаблон команд
Команды в модуле направляющие столбцов являются примерами очень распространенный шаблон в Visual Studio. Поместите связанные команды в группу, и вы поместите эту группу в главном меню, часто с "`<CommandFlag>CommandWellOnly</CommandFlag>`" присвоено скрытия команды.  Размещение команд на главных меню (таких как **изменить**) неплохо именами (такие как **Edit.AddColumnGuide**), которые полезны для поиска команд, при переназначении сочетания клавиш в **средства Параметры**. Это также полезно для получения завершения при вызове команды из **командное окно**.

Затем добавьте группу команд в контекстные меню или sub меню, где предполагается, что пользователю выполнять команды. Visual Studio обрабатывает `CommandWellOnly` как невидимости флаг для главных меню только. При размещении той же группе команд в контекстное меню или подменю, команды являются видимыми.

Как часть общий шаблон модуль направляющие столбцов создает вторую группу, содержащий один подменю. Подменю, в свою очередь, содержит первой группы с помощью команд руководство по четыре столбца. Вторая группа, содержащая подменю является многократного использования ресурса, поместить в различные контекстные меню, то помещает вложенное меню этих контекстных меню.

### <a name="the-vsct-file"></a>Vsct-файл
*.Vsct* файл объявляет команды и где они исчезают, вместе с значки и т. д. Замените содержимое файла *.vsct* файл (как описано ниже) следующим кодом:

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

**ИДЕНТИФИКАТОРЫ GUID**. Для Visual Studio можно найти обработчики команд и вызвать их, необходимо обеспечить идентификатор пакета GUID, объявленные в *ColumnGuideCommandsPackage.cs* файл (созданный из шаблона элемента проекта) совпадает с GUID объявленные в пакет *.vsct* файл (копируется из выше). Если вы повторно использовать этот пример кода, следует убедиться, что у вас другой GUID, чтобы вы не конфликтуют с всем, кто может скопировать этот код.

Найдите следующую строку в *ColumnGuideCommandsPackage.cs* и скопируйте идентификатор GUID между кавычки:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Вставьте идентификатор GUID в *.vsct* файл, чтобы получить следующую строку вашей `Symbols` объявления:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Задайте идентификаторы GUID для команды и растровый рисунок слишком должен быть уникальным для вашего расширения:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Но необходимо изменить набор команд и растровые изображения идентификаторы GUID в этом пошаговом руководстве для получения кода для работы. Идентификатор GUID должен совпадать в объявлении в набор команд *ColumnGuideCommands.cs* файл, но вы замените содержимое этого файла, слишком; таким образом, будет соответствовать идентификаторы GUID.

Другие идентификаторы GUID в *.vsct* файл определения существующего меню, к которым добавляются команды руководство по столбцу, поэтому они никогда не изменяют.

**Файл разделах**. *.Vsct* состоит из трех разделов внешнего: команд, размещения и символы. В разделе команд определяются группы команд, меню, кнопки или пункты меню и растровых изображений для значков. В разделе размещения объявляется, куда группы в меню и дополнительных размещения на существующий меню. В разделе "символы" объявляет идентификаторов, используемых в других частях *.vsct* файл, который делает *.vsct* более удобочитаемыми, чем у идентификаторы GUID и шестнадцатеричный код номера везде.

**Команд раздела, группирует определения**. В разделе команд сначала определяет группы команд. Группы команд являются команды в меню с небольшая серые линии, разделения групп. Группы также могут занять всю подменю, как в следующем примере, и вы не видите серый цвет, отделение строк в данном случае. *.Vsct* файлы Объявите две группы `GuidesMenuItemsGroup` , является потомком `IDM_VS_MENU_EDIT` (главный **изменить** меню) и `GuidesContextMenuGroup` , является потомком `IDM_VS_CTXT_CODEWIN` (код в контекстном меню редактора).

Второе объявление группы имеет `0x0600` приоритет:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

Идея состоит в поместить столбец проведет подменю в конце любого контекстного меню, к которому добавить подгруппу меню. Но, нет оснований предполагать, лучше всего знать и принудительно подменю всегда Fallback заключительным с помощью приоритет `0xFFFF`. Необходимо поэкспериментировать с номером, чтобы увидеть, где находится меню sub контекстных меню, где следует поместить. В этом случае `0x0600` достаточно велик, чтобы поместить его в конце меню, как вы видите, но оставляет место для кого-то другого для разработки своего расширения должна быть меньше расширение направляющие столбцов, если это нежелательно.

**Команды разделе определения меню**. Далее в разделе команд определяется подменю `GuidesSubMenu`, порождены в `GuidesContextMenuGroup`. `GuidesContextMenuGroup` — Это группа, добавляемые все соответствующие контекстные меню. В разделе «Размещение» код помещает группы с помощью команд руководство по четыре столбца в этом меню sub.

**Команд раздела, кнопки определения**. В разделе команд затем определяется, пункты меню или кнопки, которые представляют собой команды руководства по четыре столбца. `CommandWellOnly`, описанных выше, означает, что команды невидимы, при помещении в главном меню. Для пункта меню с двухкнопочной объявления (Добавить руководство и удалить руководство) также имеют `AllowParams` флаг:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Этот флаг обеспечивает, наряду с входящим размещения главного меню и команды для получения аргументов, когда Visual Studio вызывает обработчик команд.  Если пользователь выполняет команду в командном окне, аргумент передается в обработчик команд событий аргументы.

**Команды разделы, точечные рисунки определения**. Наконец в разделе команд объявляется точечные рисунки и значки, используемый для команд. Этот раздел представляет простое объявление, которое идентифицирует ресурс проекта и перечисляет от единицы индексы используются значки. Разделе "символы" *.vsct* файл объявляет значения идентификаторов, использовать в качестве индексов. В этом пошаговом руководстве использует набора точечных рисунков, с помощью шаблона элемента пользовательской команды добавлен в проект.

**Раздел размещения**. После команды раздел является раздел размещения. Первый из них —, где код добавляет первой группы, описанных выше, содержит четыре столбца руководство команды в меню "sub" расположения команд:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Все другие размещения `GuidesContextMenuGroup` (который содержит `GuidesSubMenu`) на другие контекстные меню редактора. Если код, объявленный `GuidesContextMenuGroup`, дочерним контекстное меню редактора кода. Вот почему вы не видите размещения для контекстного меню редактора кода.

**Символы разделе**. Как уже говорилось выше, в разделе "символы" объявляет идентификаторов, используемых в других частях *.vsct* файл, который делает *.vsct* более удобочитаемыми, чем у идентификаторы GUID и шестнадцатеричный код номера везде. Важные моменты в этом разделе описано, что идентификатор GUID пакета должно быть согласовано с объявление в классе пакета. И идентификатор GUID набора команд должны согласиться с объявлением в классе реализации команды.

## <a name="implement-the-commands"></a>Реализация команд
*ColumnGuideCommands.cs* файл реализует команды и обработчики. Когда Visual Studio загружает пакет и инициализирует его, в свою очередь вызывает пакет `Initialize` на класс реализации команд. Инициализация команды просто создает экземпляр класса, а конструктор подключает обработчик команды.

Замените содержимое файла *ColumnGuideCommands.cs* файл (как описано ниже) следующим кодом:

```csharp
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

**Исправляет ссылки**. Значит, что отсутствует ссылка на этом этапе. Нажмите правую кнопку указателя на узел "ссылки" в обозревателе решений. Выберите **добавить...**  команды. **Добавить ссылку** диалоговое окно содержит поле поиска в правом верхнем углу. Введите «редактор» (без двойных кавычек). Выберите **Microsoft.VisualStudio.Editor** элемента (вам необходимо установить флажок слева от элемента, не просто выберите элемент) и выберите **ОК** для добавления ссылки.

**Инициализация**.  При инициализации класса пакета, он вызывает `Initialize` на класс реализации команд. `ColumnGuideCommands` Инициализации создает экземпляр класса и сохраняет экземпляр класса и ссылки на пакет в члены класса.

Давайте рассмотрим один из ловушек ИБП обработчик команды из конструктора класса:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Создании `OleMenuCommand`. Visual Studio с помощью команды системы Microsoft Office. Аргументы ключа при создании экземпляра `OleMenuCommand` — функция, которая реализует команду (`AddColumnGuideExecuted`), функция, вызываемая при Visual Studio отображается меню с помощью команды (`AddColumnGuideBeforeQueryStatus`) и идентификатор команды. Visual studio вызывает функцию запроса состояния перед отображением команды меню, что команда сам невидимым или недоступен для выбора для отображения меню (например, отключение **копирования** Если ничего не выбрано), изменить его значок или даже изменить его имя (например, добавить что-либо удалите что-нибудь) и так далее. Идентификатор команды, должен соответствовать идентификатор объявлен в команду *.vsct* файла. Добавьте строки для набора команд и направляющие столбцов команды должны совпадать *.vsct* файл и *ColumnGuideCommands.cs*.

Следующая строка предоставляет помощь по при пользователей вызвать команду с помощью окне командной строки (см. ниже):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Запросить состояние**. Функции состояния запроса `AddColumnGuideBeforeQueryStatus` и `RemoveColumnGuideBeforeQueryStatus` проверить некоторые параметры (например, максимальное количество руководства или столбец max) или же если структуру столбца для удаления. Они позволяют выполнять команды Если условиям.  Функции состояния запроса должны быть эффективным, так как они выполняются каждый раз, когда Visual Studio отображается меню и для каждой команды меню.

 **Функция AddColumnGuideExecuted**. Интересная часть Добавление руководство является выяснение текущее представление редактора расположение курсора.  Во-первых, эта функция вызывает `GetApplicableColumn`, который проверяет, если аргумент, предоставленный пользователем в аргументах событий обработчик команд, и если такового не имеется, функция проверяет представление редактора:

```csharp
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

`GetCurrentEditorColumn` имеет потребуются для верного <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> представления кода.  Если вы выполните трассировку `GetActiveTextView`, `GetActiveView`, и `GetTextViewFromVsTextView`, можно увидеть, как это сделать. Ниже приведен соответствующий код абстрагируется, начиная с текущего выделения, получение фрейма выделения, а затем получение DocView рамки как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, затем получение <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> из IVsTextView, а затем узел представления, получение и Наконец IWpfTextView:

```csharp
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

Получив IWpfTextView, вы можете получить столбец, где находится курсор:

```csharp
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

С помощью текущего столбца в стороны там, где пользователь щелкнул, код просто вызывает на диспетчер параметров для добавления или удаления столбца. Диспетчер параметров запускает событие для которой все `ColumnGuideAdornment` прослушивания объектов. При возникновении события, эти объекты поменять свои взгляды связанный текст с новыми настройками руководство столбца.

## <a name="invoke-command-from-the-command-window"></a>Вызвать команду из окна команд
Пример направляющие столбцов позволяет пользователям вызывать две команды в командном окне как форма расширяемости. Если вы используете **представление &#124; Other Windows &#124; командное окно** команды видно в окне командной строки. Вы можете взаимодействовать с окне командной строки, введя «изменить», и с помощью команды завершения имени и предоставление аргумент 120, у вас есть следующий результат:

```csharp
> Edit.AddColumnGuide 120
>
```

Составляющие этого примера находятся в *.vsct* файл объявления, `ColumnGuideCommands` конструктор класса, когда он подключает обработчиков команд, а также реализации обработчика команд, которые проверяют аргументы события.

Вы видели "`<CommandFlag>CommandWellOnly</CommandFlag>`" в *.vsct* файл, а также места размещения в **изменить** несмотря на то, что команды не отображаются в главном меню **изменить** меню пользовательского интерфейса. Они имеются в основном **изменить** меню дает им имена, такие как **Edit.AddColumnGuide**. Объявление группы команд, которое содержит четыре команды уделено группе **изменить** непосредственно меню:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

В разделе кнопки объявлена команды `CommandWellOnly` остаться невидимым в главном меню и их с объявил `AllowParams`:

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

Вы видели подключить код в обработчик команд `ColumnGuideCommands` конструктор класса представленное описание допустимых параметров:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

Вы видели `GetApplicableColumn` функцию проверки `OleMenuCmdEventArgs` для значения перед проверкой представление редактора для текущего столбца:

```csharp
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

## <a name="try-your-extension"></a>Попробуйте расширения
Теперь можно нажать клавиши **F5** для выполнения расширения направляющие столбцов. Откройте текстовый файл и используйте контекстное меню редактора Добавление направляющих, удалить их и изменить их цвет. Щелкните текст (пробелы не пройден конец строки) для добавления столбца руководство или редактор добавляет его в последний столбец в строке. Если вы используете командное окно и вызывать команды с аргументом, можно добавить направляющие столбцов в любом месте.

Если вы хотите попробовать разные команды размещения, измените имена, изменение значков и т. д., и у вас возникли проблемы с Visual Studio отображает последнюю версию кода в меню, вы можете Сбросить экспериментальный куст, в котором отладки. Подключите **меню "Пуск" Windows** и введите «Сброс». Найдите и выполните команду, **Сброс Далее экспериментального экземпляра Visual Studio**. Эта команда удаляет экспериментальном кусте реестра всех компонентов расширения. Это не так Очистка out параметры из компонентов, поэтому все руководства, у вас когда вы завершаете работу экспериментальном кусте Visual Studio по-прежнему существуют когда ваш код считывает хранилища параметров при следующем запуске.

## <a name="finished-code-project"></a>Готовый код проекта
Скоро будет проект GitHub примеров расширения среды Visual Studio и завершенного проекта будет здесь. В этой статье будут обновляться для указания существует, когда это происходит. Готовый пример проекта могут иметь разные идентификаторы GUID и будет иметь полоса различными растровыми изображениями для значки команд.

Вы можете опробовать версию функции направляющие столбец с данной коллекцией Visual Studio[расширение](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines).

## <a name="see-also"></a>См. также
- [В редакторе](../extensibility/inside-the-editor.md)
- [Расширение редактора и языковой службы](../extensibility/extending-the-editor-and-language-services.md)
- [Точки расширения редактора и служба языка](../extensibility/language-service-and-editor-extension-points.md)
- [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)
- [Добавление подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md)
- [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md)
