---
title: Создание украшения представления, команды и настройки (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4aab9e0ede95eebe6f8f54cc3f01e7e7d5f98d1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697648"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>Прохождение: Создание украшения представления, команд и настроек (направляющие колонки)
Вы можете расширить текстовый/код-редактор Visual Studio с командами и эффектами просмотра. В этой статье показано, как начать работу с популярной функцией расширения, колонки руководства. Направляющие столбцы представляют собой визуальные линии света, нарисованные на представлении редактора текста, чтобы помочь вам управлять кодом до определенной ширины столбца. В частности, отформатированный код может быть важен для образцов, которые вы включаете в документы, сообщения в блогах или отчетах об ошибках.

В этом пошаговом руководстве описаны следующие операции:
- Создание проекта VSIX
- Добавление украшения представления редактора
- Добавьте поддержку для сохранения и получения настроек (где нарисовать направляющие столбцы и их цвет)
- Добавить команды (добавить/удалить направляющие столбцы, изменить их цвет)
- Разместите команды в меню Редактирования и меню контекста текстовых документов
- Добавить поддержку для вызывая команды из окна команды Visual Studio

  Вы можете попробовать версию функции руководства колонки с этим[расширением](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)Visual Studio Gallery.

  > [!NOTE]
  > В этом пошаговом шаге вы вставляете большое количество кода в несколько файлов, генерируемых шаблонами расширения Visual Studio. Но, скоро это пошаговоцрешение будет относиться к завершенным решением на GitHub с другими примерами расширения. Завершенный код немного отличается тем, что он имеет реальные значки команд вместо использования иконок generictemplate.

## <a name="get-started"></a>Начало работы
Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="set-up-the-solution"></a>Настройка решения
Сначала вы создаете проект VSIX, добавляете украшение представления редактора, а затем добавляете команду (которая добавляет VSPackage для владения командой). Основная архитектура заключается в следующем:
- У вас есть слушатель создания `ColumnGuideAdornment` текстового представления, который создает объект в представлении. Этот объект при необходимости слушает события об изменении представления или изменения параметров, обновление или перерисовку столбцов.
- Там в `GuidesSettingsManager` том, что обрабатывает чтение и письмо из настройки Visual Studio хранения. Менеджер настроек также имеет операции для обновления настроек, поддерживающих команды пользователя (добавить столбец, удалить столбец, изменить цвет).
- Пакет VSIP необходим, если у вас есть команды пользователя, но это просто шаблонный код, который инициализирует объект реализации команд.
- Есть `ColumnGuideCommands` объект, который выполняет команды пользователя и подключает обработчики команд для команд, заявленных в файле *.vsct.*

  **VSIX**. Используйте **команду File &#124; New...** Выберите узло **расширяемости** под **C в** левом навигационном стекле и выберите **проект VSIX** в правом стекле. Введите название **ColumnGuides** и выберите **OK** для создания проекта.

  **Посмотреть украшение**. Нажмите кнопку указателя на узло проекта в solution Explorer. Выберите **команду Добавить &#124; новый элемент,** чтобы добавить новый элемент украшения представления. Выберите **&#124; редактора** в левом навигационном стеле и выберите **украшение Viewport** в правом стеле. Введите имя **ColumnGuideAdornment** в качестве имени элемента и **выберите добавить** его.

  Вы можете увидеть этот шаблон элемента добавлены два файла в проект (а также ссылки, и так далее): **ColumnGuideAdornment.cs** и **ColumnGuideAdornmentTextViewCreationListener.cs**. Шаблоны рисуют фиолетовый прямоугольник на представлении. В следующем разделе вы измените пару строк в представлении создания слушателя и замените содержимое **ColumnGuideAdornment.cs**.

  **Команды**. В **Solution Explorer**нажмите кнопку «Правый указатель» на узло проекта. Выберите **команду Добавить &#124; новый элемент,** чтобы добавить новый элемент украшения представления. Выберите **расширяемость &#124; VSPackage** в левом навигационном стеле и выберите **Custom Command** в правом стене. Введите имя **ColumnGuides** в качестве имени элемента и **выберите Добавить.** В дополнение к нескольким ссылкам, добавив команды и пакет также **добавлены ColumnGuideCommands.cs,** **ColumnGuideCommandsPackage.cs,** и **ColumnGuideCommandsPackage.vsct**. В следующем разделе вы заменяете содержимое первого и последнего файлов для определения и реализации команд.

## <a name="set-up-the-text-view-creation-listener"></a>Настройка слушателя создания текстового представления
Открыть *ColumnGuideAdornmentTextViewCreationListener.cs* в редакторе. Этот код реализует обработчик для всякий раз, когда Visual Studio создает текстовые представления. Есть атрибуты, которые управляют, когда обработчик вызывается в зависимости от характеристик представления.

Код также должен декларировать слой украшения. Когда редактор обновляет представления, он получает слои украшения для представления и от этого получает элементы украшения. Вы можете объявить заказ вашего слоя по отношению к другим с атрибутами. Замените следующую строку:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

с этими двумя строками:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

Линия, которую вы заменили, находится в группе атрибутов, которые объявляют слой украшения. Первая строка, измененная, изменяется только там, где появляются направляющие строки столбцов. Рисование строк "до" текста в представлении означает, что они отображаются позади или ниже текста. Вторая строка заявляет, что украшения руководства столбца применимы к текстовым объектам, которые соответствуют вашему понятию документа, но можно объявить украшение, например, работать только для редактирования текста. В [пунктах расширения языкового сервиса и редактора](../extensibility/language-service-and-editor-extension-points.md) есть больше информации

## <a name="implement-the-settings-manager"></a>Реализация менеджера настроек
Замените содержимое *GuidesSettingsManager.cs* следующим кодом (объясняется ниже):

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

Большая часть этого кода создает и разбирает формат\<настроек: "RGB (int>,\<int>,\<int>) \<int>, \<int>, ...".  В конце — это одноэтажные столбцы, где нужны направляющие колонки. Колонка направляет расширение, фиксируя все его параметры в одной строке значения настройки.

Есть некоторые части кода стоит выделить. Следующая строка кода получает управляемую обертку Visual Studio для хранения настроек. По большей части, это абстрагируется от реестра Windows, но этот API не зависит от механизма хранения.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

Хранилище параметров Visual Studio использует идентификатор категории и идентификатор настройки для однозначного определения всех настроек:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

Вы не должны `"Text Editor"` использовать в качестве имени категории. Вы можете выбрать все, что вам нравится.

Первые несколько функций являются точками входа для изменения настроек. Они проверяют ограничения высокого уровня, такие как максимальное количество разрешенных руководств.  Затем они `WriteSettings`вызывают, который составляет строку настроек и устанавливает свойство. `GuideLinesConfiguration` Настройка этого свойства сохраняет значение настроек для хранения `SettingsChanged` настроек Visual `ColumnGuideAdornment` Studio и запускает событие для обновления всех объектов, каждый из которых связан с текстовым представлением.

Есть несколько функций точки входа, таких как `CanAddGuideline`, которые используются для реализации команд, которые меняют настройки. Когда Visual Studio показывает меню, она запрашивает реализации команд, чтобы увидеть, включена ли команда в настоящее время, как ее имя и так далее.  Ниже вы можете подключить эти точки входа для реализации команд. Для получения дополнительной информации [Extend menus and commands](../extensibility/extending-menus-and-commands.md)о командах см.

## <a name="implement-the-columnguideadornment-class"></a>Реализация класса ColumnGuideAdornment
Класс `ColumnGuideAdornment` мгновенно подходит для каждого текстового представления, которое может иметь украшения. Этот класс слушает события об изменении представления или изменения параметров, а также о необходимости руководства по обновлению или перерисовке столбцов.

Замените содержимое *ColumnGuideAdornment.cs* следующим кодом (объясняется ниже):

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

Инстанции этого класса удерживают <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> связанный и `Line` список объектов, нарисованных на представлении.

Конструктор (вызывается `ColumnGuideAdornmentTextViewCreationListener` с момента создания Visual Studio новых `Line` представлений) создает объекты направляющих столбцов.  Конструктор также добавляет обработчики для `SettingsChanged` `GuidesSettingsManager`события (определяется `LayoutChanged` `Closed`в) и событий представления и .

Событие `LayoutChanged` запускается из-за нескольких видов изменений в представлении, в том числе при созданием представления Visual Studio. `OnViewLayoutChanged` Обработчик `AddGuidelinesToAdornmentLayer` вызывает для выполнения. Код определяет, `OnViewLayoutChanged` нужно ли обновлять позиции строки на основе изменений, таких как изменения размера шрифта, ретентеры представления, горизонтальная прокрутка и так далее. Код в `UpdatePositions` вызывает направляющие строки, чтобы нарисовать между символами или сразу после столбца текста, который находится в указанном символе смещения в строке текста.

Всякий раз, `SettingsChanged` когда настройки изменения `Line` функции просто воссоздает все объекты с любыми новыми настройками. После установки позиций строки код `Line` удаляет `ColumnGuideAdornment` все предыдущие объекты из слоя украшения и добавляет новые.

## <a name="define-the-commands-menus-and-menu-placements"></a>Определение команд, меню и размещения меню
Объявление команд и меню может быть многодляное, размещение групп команд или меню в различных других меню и подключение обработчиков команд. В этом пошаговом показании рассказывается о том, как работают команды в этом расширении, но для получения более подробной [информации см.](../extensibility/extending-menus-and-commands.md)

### <a name="introduction-to-the-code"></a>Введение в код
Расширение Column Guides показывает объявление группы команд, которые принадлежат друг другу (добавить столбец, удалить столбец, изменить цвет строки), а затем поместить эту группу в подменю контекстного меню редактора.  Расширение Колонки Руководства также добавляет команды в основное меню **edit,** но держит их невидимыми, обсуждается как общий шаблон ниже.

В реализации команд есть три части: ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage.vsct и ColumnGuideCommands.cs. Код, генерируемый шаблонами, помещает команду в меню **Tools,** которое появляется в диалоговом поле в качестве реализации. Вы можете посмотреть, как это реализуется в *.vsct* и *ColumnGuideCommands.cs* файлов, так как это просто. Вы заменяете код в этих файлах ниже.

Код пакета содержит шаблонные декларации, необходимые visual Studio, чтобы обнаружить, что расширение предлагает команды и найти, где разместить команды. Когда пакет инициализируется, он мгновенно примкнет к классу реализации команд. Для получения дополнительной информации о пакетах, относящихся к командам, [см.](../extensibility/extending-menus-and-commands.md)

### <a name="a-common-commands-pattern"></a>Общий шаблон команд
Команды в расширении Колонка Руководства являются примером очень распространенный шаблон в Visual Studio. Вы помещаете связанные команды в группу, и вы`<CommandFlag>CommandWellOnly</CommandFlag>`помещаете эту группу в главное меню, часто с «набором, чтобы сделать команду невидимой.  Ввод команд в основные меню (например, **Edit**) дает им хорошие имена (например, **Edit.AddColumnGuide),** которые полезны для поиска команд при повторном назначении ключевых привязок в **параметры инструментов.** Это также полезно для получения завершения при входе команды из **окна команды.**

Затем группа команд добавляется в контекстные меню или подменю, где пользователь ожидает, что пользователь будет использовать команды. Visual Studio `CommandWellOnly` рассматривает как флаг невидимости только для основных меню. При размещании одной и той же группы команд в контекстном меню или подменю будут видны команды.

В рамках общего шаблона расширение Колонка Руководства создает вторую группу, которая содержит единое меню подлодки. Подменю, в свою очередь, содержит первую группу с командами руководства из четырех столбцов. Вторая группа, в которой находится меню подлодки, — это многоразовый актив, который вы размещаете в различных контекстных меню, что помещает подменю в эти контекстные меню.

### <a name="the-vsct-file"></a>Файл .vsct
Файл *«vsct»* объявляет команды и то, куда они идут, вместе с иконками и так далее. Замените содержимое файла *.vsct* следующим кодом (объясняется ниже):

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

**GUIDS**. Для того, чтобы Visual Studio нашла обработчики команд и вызвала их, необходимо обеспечить, чтобы пакет GUID, объявленный в *ColumnGuideCommandsPackage.cs* файле (сгенерированном из шаблона элемента проекта), соответствовал пакету GUID, объявленного в файле *.vsct* (скопированный сверху). Если вы повторно используете этот пример кода, вы должны убедиться, что у вас есть другой GUID, чтобы вы не конфликтовали с кем-либо еще, кто, возможно, скопировал этот код.

Найдите эту строку в *ColumnGuideCommandsPackage.cs* и скопируйте GUID между кавычками:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Затем вставьте GUID в файл *.vsct,* чтобы у вас `Symbols` была следующая строка в декларациях:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

GUIDs для набора команд и файл изображения bitmap также должны быть уникальными для ваших расширений:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Но вам не нужно менять набор команд и изображения bitmap GUIDs в этом пошаговое руководство, чтобы заставить код работать. Набор команд GUID должен соответствовать декларации в *ColumnGuideCommands.cs* файле, но вы заменяете содержимое этого файла; таким образом, GUIDs будет соответствовать.

Другие GUID в файле *.vsct* определяют уже существующие меню, к которым добавляются команды руководства столбца, поэтому они никогда не меняются.

**Разделы файлов**. *Vsct* имеет три внешние разделы: команды, размещения и символы. Раздел команд определяет группы команд, меню, кнопки или элементы меню, а также бит-карты для иконок. В разделе размещения декларируется, где группы выходят в меню или дополнительные места размещения в уже существующие меню. Раздел символов объявляет идентификаторы, используемые в другом месте в файле *.vsct,* что делает код *.vsct* более читаемым, чем наличие GUID и hex номеров во всем мире.

**Раздел команд, определения групп.** Раздел команд сначала определяет командные группы. Группы команд — это команды, которые вы видите в меню с небольшими серыми линиями, разделяющими группы. Группа может также заполнить все меню под, как в этом примере, и вы не видите серые разделительные линии в этом случае. Файлы *.vsct* объявляют `GuidesMenuItemsGroup` две группы, `IDM_VS_MENU_EDIT` которые являются родительскими (основное меню **edit)** и `GuidesContextMenuGroup` которые являются родительскими `IDM_VS_CTXT_CODEWIN` (меню контекста редактора кода).

Вторая групповая `0x0600` декларация имеет приоритет:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

Идея заключается в том, чтобы поместить подменю руководств столбца в конце любого контекстного меню, к которому вы добавляете группу подменю. Но, вы не должны предположить, что вы знаете лучше и заставить под меню всегда быть последним, используя приоритет `0xFFFF`. Вы должны экспериментировать с номером, чтобы увидеть, где ваше подменю находится на контекстменю, где вы поместите его. В этом `0x0600` случае, достаточно высока, чтобы положить его в конце меню, насколько вы можете видеть, но он оставляет место для кого-то еще, чтобы разработать их расширение будет ниже, чем расширение столбцов руководства, если это желательно.

**Раздел команд, определение меню**. Далее раздел команды определяет меню `GuidesSubMenu`подки, `GuidesContextMenuGroup`пристежоченное к меню . Это `GuidesContextMenuGroup` группа, которая добавляется ко всем соответствующим контекстным меню. В разделе размещения код помещает группу с командами руководства из четырех столбцов в этом меню подлодки.

**Раздел команд, определения кнопок**. Затем раздел команд определяет элементы меню или кнопки, которые являются командами руководства из четырех столбцов. `CommandWellOnly`, обсуждается выше, означает, что команды невидимы при размещении в главном меню. Два из пунктов меню кнопки декларации (добавить `AllowParams` руководство и удалить руководство) также имеют флаг:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Этот флаг позволяет, наряду с наличием основных мест размещения меню, команда получать аргументы, когда Visual Studio вызывает обработчик команды.  Если пользователь запускает команду из окна команды, аргумент передается обработчику команды в аргументах события.

**Разделы команд, определения биткарт**. Наконец, в разделе команд декларируются бит-карты или значки, используемые для команд. Этот раздел представляет собой простое заявление, которое определяет ресурс проекта и перечисляет однозначные индексы используемых иконок. Раздел символов файла *.vsct* объявляет значения идентификаторов, используемых в качестве индексов. В этом пошаговом пошаговом пункте используется полоса bitmap, снабженная пользовательским шаблоном элемента команд, добавленным в проект.

**Раздел размещения**. После раздела команд раздел размещения. Первый — это место, где код добавляет первую обсуждаемую группу, в которой содержится команды руководства из четырех столбцов в меню подлодки, где появляются команды:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Все другие размещения добавить `GuidesContextMenuGroup` (который `GuidesSubMenu`содержит ) в других меню контекста редактора. Когда код `GuidesContextMenuGroup`объявил, он был пригнан к контекстному меню редактора кода. Вот почему вы не видите размещения для контекстного меню редактора кода.

**Раздел символов**. Как указано выше, раздел символов декларирует идентификаторы, используемые в другом месте в файле *.vsct,* что делает код *.vsct* более читаемым, чем guiDs и hex номера во всем мире. Важным моментом в этом разделе является то, что пакет GUID должен согласиться с декларацией в классе пакетов. Кроме того, набор команд GUID должен согласовываться с декларацией в классе реализации команды.

## <a name="implement-the-commands"></a>Реализация команд
Файл *ColumnGuideCommands.cs* реализует команды и подключает обработчики. Когда Visual Studio загружает пакет и инициализирует его, пакет, в свою очередь, призывает `Initialize` класс реализации команд. Инициализация команд просто мгновения класса, и конструктор подключает все обработчики команд.

Замените содержимое *ColumnGuideCommands.cs* файла следующим кодом (объясняется ниже):

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

**Исправление ссылок**. Вы упускаете ссылку на данный момент. Нажмите кнопку указателя на узло ссылки в Solution Explorer. Выберите команду **Добавить ...** Диалог **Add Reference** имеет поле поиска в правом верхнем углу. Введите "редактор" (без двойных котировок). Выберите элемент **Microsoft.VisualStudio.Editor** (вы должны проверить поле слева от элемента, а не просто выбрать элемент) и выбрать **OK,** чтобы добавить ссылку.

**Инициализация**.  Когда класс пакетов инициализируется, он вызывает `Initialize` класс реализации команд. Инициализация `ColumnGuideCommands` мгновенно сохраняет класс и ссылку на пакет в членах класса.

Давайте посмотрим на один из подсобий обработчика команд от конструктора класса:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Вы создаете `OleMenuCommand`. Visual Studio использует командную систему Microsoft Office. Ключевыми аргументами при мгновенном `OleMenuCommand` воспроизведении является функция,`AddColumnGuideExecuted`которая реализует команду ( ), функция вызова,`AddColumnGuideBeforeQueryStatus`когда Visual Studio показывает меню с командой ( ) и идентификатор команды. Visual studio вызывает функцию статуса запроса перед показом команды в меню, чтобы команда сделать себя невидимой или серой для конкретного отображения меню (например, отключение **Copy,** если нет выбора), изменить его значок, или даже изменить его имя (например, от Добавить что-то удалить что-то), и так далее. Идентификатор команды должен соответствовать идентификатору команды, объявленного в файле *.vsct.* Строки для набора команд и направляющие колонки добавляют, что команда должна совпадать между файлом *.vsct* и *ColumnGuideCommands.cs.*

Следующая строка предоставляет помощь, когда пользователи вызывают команду через окно команды (объясняется ниже):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Статус запроса**. Функции статуса `AddColumnGuideBeforeQueryStatus` `RemoveColumnGuideBeforeQueryStatus` запроса и проверяют некоторые настройки (например, максимальное количество направляющих или максимальный столбец) или если есть руководство столбца для удаления. Они позволяют командам, если условия правильные.  Функции статуса запроса должны быть эффективными, поскольку они работают каждый раз, когда Visual Studio показывает меню и для каждой команды в меню.

 **ДобавитьФункция «КолполГИГид»**. Интересная часть добавления руководства выяснить текущий вид редактора и caret местоположение.  Во-первых, `GetApplicableColumn`эта функция вызывает, который проверяет, есть ли аргумент, поставляемый пользователем в аргументах события обработчика команды, и если его нет, функция проверяет представление редактора:

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

`GetCurrentEditorColumn`нужно немного выкопать, <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> чтобы получить представление о коде.  Если `GetActiveTextView`проследить, `GetActiveView`и `GetTextViewFromVsTextView`, вы можете увидеть, как это сделать. Следующий код является соответствующим кодом абстрагируется, начиная с текущего выбора, затем получить кадр <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>выбора, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> а затем получить кадр DocView как , то получить от IVsTextView, то получить вид хозяина, и, наконец, IWpfTextView:

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

Если у вас есть IWpfTextView, вы можете получить колонку, где находится caret:

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

При нажатии на кнопку текущей колонки, на которой пользователь нажал, код просто призывает менеджера настроек добавить или удалить столбец. Менеджер настроек запускает событие, `ColumnGuideAdornment` к которому слушают все объекты. При сходе события эти объекты обновляют связанные с ними текстовые представления новыми настройками наведения столбцов.

## <a name="invoke-command-from-the-command-window"></a>Вызвать команду из окна командования
Образец руководств столбца позволяет пользователям вызывать две команды из окна командования в качестве одной из форм расширяемости. Если вы используете представление &#124; другие команды **Windows &#124; командного окна,** вы можете увидеть окно команды. Вы можете взаимодействовать с окном командования, введя "отодвинуть", а при завершении командного имени и поставке аргумента 120 у вас есть следующий результат:

```csharp
> Edit.AddColumnGuide 120
>
```

Части образца, которые позволяют это поведение, находятся в `ColumnGuideCommands` файловых декларациях *.vsct,* конструкторе класса, когда он подключает обработчики команд, и реализации обработчика команд, которые проверяют аргументы событий.

Вы видели`<CommandFlag>CommandWellOnly</CommandFlag>`" в *файле .vsct,* а также размещения в главном меню **Edit,** даже если команды не отображаются в uI меню **Edit.** Имея их на основной **edit** меню дает им имена, как **Edit.AddColumnGuide**. Объявление группы команд, вмещаев в себя четыре команды, поместило группу в меню **Edit** непосредственно:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

Раздел кнопок позже `CommandWellOnly` объявил команды, чтобы держать их `AllowParams`невидимыми в главном меню и объявил их с:

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

Вы видели, как обработчик `ColumnGuideCommands` команды подключил код в конструкторе класса, при условии описания допустимого параметра:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

Вы видели `GetApplicableColumn` проверку `OleMenuCmdEventArgs` функции на наличие значения перед проверкой представления редактора для текущего столбца:

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

## <a name="try-your-extension"></a>Попробуйте расширение
Теперь вы можете нажать **F5,** чтобы выполнить расширение колонки Руководства. Откройте текстовый файл и используйте контекстное меню редактора, чтобы добавить направляющие строки, удалить их и изменить их цвет. Нажмите в тексте (не пробел прошел конец строки), чтобы добавить руководство столбца, или редактор добавляет его в последнюю колонку на линии. Если вы используете окно команды и вызываете команды с аргументом, вы можете добавить направляющие столбцы в любом месте.

Если вы хотите попробовать различные размещения команд, изменить имена, изменить значки и так далее, и у вас есть какие-либо проблемы с Visual Studio, показывающий вам последний код в меню, вы можете сбросить экспериментальный улей, в котором вы отладоки. Подведите **меню Windows Start** и введите "перезагрузку". Ищите и запускать команду, **сбросить следующую экспериментальную студию Visual Studio.** Эта команда очищает экспериментальный улей реестра всех компонентов расширения. Он не очищает настройки от компонентов, так что любые руководства у вас, когда вы выключили Visual Studio экспериментальных улья все еще там, когда ваш код читает настройки магазина на следующий запуск.

## <a name="finished-code-project"></a>Готовый код проекта
В скором времени будет GitHub проект Visual Studio Extensibility образцов, и завершенный проект будет там. Эта статья будет обновлена, чтобы указать там, когда это произойдет. Завершенный проект образца может иметь различные гиды и будет иметь различные полосы бит-карт для значков команд.

Вы можете попробовать версию функции руководства колонки с этим[расширением](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)Visual Studio Gallery.

## <a name="see-also"></a>См. также
- [Внутри редактора](../extensibility/inside-the-editor.md)
- [Расширить службы редактора и языка](../extensibility/extending-the-editor-and-language-services.md)
- [Языковой сервис и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)
- [Расширить меню и команды](../extensibility/extending-menus-and-commands.md)
- [Добавить подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md)
- [Создание расширения с шаблоном элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md)
