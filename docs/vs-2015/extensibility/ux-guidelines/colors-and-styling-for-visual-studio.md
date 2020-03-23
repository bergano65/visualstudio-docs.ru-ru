---
title: Настройка цветов и стиля
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0330ef80fc1127893590ef8d326cb5b8e0cf0160
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301347"
---
# <a name="colors-and-styling-for-visual-studio"></a>Цвета и стили для Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="using-color-in-visual-studio"></a>Использование цвета в Visual Studio
 В Visual Studio цвет используется в основном как средство коммуникации, а не только как украшение. Используйте цвет минимально и зарезервируйте его для ситуаций, когда вы хотите:

- Общайтесь со значением или принадлежностью (например, платформеили или модификаторами языка)

- Привлечь внимание (например, указывать на изменение статуса)

- Улучшение читаемости и предоставление ориентиров для навигации по uI

- Увеличение желательности

  Существует несколько вариантов присвоения цветов элементам uI в Visual Studio. Иногда бывает трудно понять, какой вариант вы должны использовать, или как использовать его правильно. Эта тема поможет вам:

1. Понять различные услуги и системы, используемые для определения цветов в Visual Studio.

2. Выберите правильный вариант для данного элемента.

3. Правильно используйте выбранный вами вариант.

   **ВАЖНО:** Никогда не жесткий код hex, RGB или системных цветов для элементов uI. Использование услуг обеспечивает гибкость в настройке оттенка. Кроме того, без сервиса вы не сможете воспользоваться возможностями переключения тем [ы службы VSColor.](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Методы присвоения цвета элементам интерфейса Visual Studio
 Выберите метод, наиболее подходящий для элементов uI.

|Ваш uI|Метод|Что это такое?|
|-------------|------------|--------------------|
|Вы встроили или автономные диалоговые коробки.|**Системные цвета**|Системные имена, позволяющие операционной системе определять цвет и внешний вид элементов совместного использования, например для общего управления диалогом.|
|У вас есть пользовательский пользовательский пользовательский элемент, который вы хотите соответствовать общей среде VS, и у вас есть элементы пользовательского развиза, которые соответствуют категории и смысловому значению общих токенов.|**Общие общие цвета**|Существующие предопределенные имена маркеров цвета для конкретных элементов uI|
|У вас есть отдельная функция или группа функций, и нет общего цвета для подобных элементов.|**Пользовательские цвета**|Имена маркеров цвета, которые специфичны для области и не предназначены для совместного использования с другим иском|
|Необходимо разрешить конечному пользователю настроить пользовательский интерфейс или содержимое (например, для текстовых редакторов или специализированных дизайнерских окон).|**Настройка конечных пользователей**<br /><br /> **(Инструменты > диалог опций)**|Настройки, определенные на странице "Ленты и цвета" в диалоге **"Инструменты > опции"** или специализированной странице, специфичной для одной функции uI.|

### <a name="visual-studio-themes"></a>Темы визуальной студии
 Visual Studio имеет три различные цветовые темы: светлые, темные и синие. Он также обнаруживает режим high Contrast, который является общесистемной цветовой темой, предназначенной для доступности.

 Пользователи побудили выбрать тему во время их первого использования Visual Studio и могут переключить темы позже, перейдя на **инструменты > варианты > среды > целом** и выбирая новую тему из "цветной темы" dropdown меню.

 Пользователи также могут использовать панель управления, чтобы переключить все свои системы в одну из нескольких тем с высоким контрастом. Если пользователь выбирает тему High Contrast, то селектор темы цвета Visual Studio больше не влияет на цвета в Visual Studio, хотя любые изменения темы сохраняются, когда пользователь выходит из режима High Contrast. Для получения дополнительной информации о режиме High Contrast [см.](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)

### <a name="the-vscolor-service"></a>Услуга VSColor
 Visual Studio предоставляет услугу цвета среды, известную как служба VSColor, которая позволяет связывать цветовые значения элементов вашего uI с названной записью, содержащей цветовые значения для каждой темы Visual Studio. Это гарантирует, что ваши цвета будут автоматически меняться, чтобы отразить текущую тему, выбранную пользователем или режим высокой контрастности. Использование службы означает, что реализация всех связанных с темой изменений цвета обрабатывается в одном месте, и если вы используете общие общие цвета из службы, ваш uI автоматически будет отражать новые темы в будущих версиях Visual Studio.

### <a name="implementation"></a>Реализация
 Исходный код Visual Studio включает в себя несколько файлов определения пакетов, которые содержат списки имен токенов и соответствующие значения цвета для каждой темы. Служба цветов считывает VSColors, определенные в этих файлах определения пакетов. Эти цвета упоминаются в xAML разметке или в коде, а затем загружаются либо через метод **IVsUIShell5.GetThemedColor** или отображение DynamicResource.

### <a name="system-colors"></a>Системные цвета
 Общие элементы управления ссылаются на цвета системы по умолчанию. Если вы хотите, чтобы ваш чат использовал цвета системы, например, когда вы создаете встроенный или автономный диалог, вам не нужно ничего делать.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Общие общие цвета в службе VSColor
 Элементы интерфейса должны отражать общую среду Visual Studio. Повторное использование общих цветов, подходящих для разработанного компонента интерфейса, вы гарантируете, что ваш интерфейс соответствует другим интерфейсам Visual Studio и что ваши цвета будут обновляться автоматически при добавлении или обновлении тем.

 Прежде чем использовать общие общие цвета, убедитесь, что вы понимаете, как правильно их использовать. Неправильное использование общих общих цветов может привести к непоследовательной, разочарование, или запутанной опыт для ваших пользователей.

### <a name="user-customizable-colors"></a>Настраиваемые цвета, настраиваемые пользователями
 См.: [Разоблачение цветов для конечных пользователей](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

 Иногда необходимо разрешить конечному пользователю настроить пользовательский интерфейс, например, при создании редактора кода или поверхности дизайна. Настраиваемые компоненты пользовательского опыта можно найти в разделе **шрифты и цвета** диалога **«Инструменты > параметры»,** где пользователи могут изменить цвет переднего плана, цвет фона или и то, и другое.

 ![Инструменты &#62; варианты диалога в визуальной студии](../../extensibility/ux-guidelines/media/0301-a-toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")

 **Диалог инструментов>варианты**

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a>Служба VSColor
 Visual Studio предоставляет услугу цвета среды, также называемую службой VSColor или службой цвета оболочки. Эта услуга позволяет связать цветовые значения элементов uI с набором цветов, содержащим цвета для каждой темы. Служба VSColor должна использоваться для всех элементов пользовательского интерфейса, чтобы цвета автоматически менялись, чтобы отразить текущую выбранную пользователем тему, и чтобы пользовательский интерфейс, привязанный к службе цвета среды, интегрировался с новыми темами в будущих версиях Visual Studio.

### <a name="how-the-service-works"></a>Как работает служба
 Служба цвета среды читает VSColors, определенные в .pkgdef для компонента uI. Эти VSColors затем ссылаются в XAML разметки или кода и загружаются через либо **IVsUIShell5.GetThemedColor** или картографирование DynamicResource.

 ![Архитектура службы цвета среды разработки](../../extensibility/ux-guidelines/media/0302-a-environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")

 **Архитектура службы цвета среды разработки**

### <a name="accessing-the-service"></a>Доступ к службе
 Существует несколько различных способов доступа к службе VSColor, в зависимости от того, какие цветовые токены вы используете и какой код у вас есть.

#### <a name="predefined-environment-colors"></a>Предопределенные цвета среды

##### <a name="from-native-code"></a>Из родного кода
 Оболочка предоставляет услугу, которая дает доступ к COLORREF цветов. Услуга/интерфейс:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

 В файле VSShell80.idl __VSSYSCOLOREX перечисления **имеет** константы цвета оболочки. Чтобы использовать его, пройти в качестве значения индекса либо одно из значений из enum __VSSYSCOLOREX документированы в MSDN или регулярный номер индекса, что система Windows API, **GetSysColor**, принимает. Это возвращает значение RGB цвета, которое должно быть использовано во втором параметре.

 При хранении ручки или кисти с новым цветом, вы должны adviseBroadcastMessages (от оболочки Visual Studio) и слушать WM_SYSCOLORCHANGE и WM_THEMECHANGED сообщений.

```
// To access the color service in native code, you'll make a call that resembles this:
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);

```

 **ПРИМЕЧАНИЕ:** Значения COLORREF, возвращенные **GetVSSysColorEx()** содержат только R,G,B компоненты тематиного цвета. Если запись темы использует прозрачность, значение альфа-канала отбрасывается перед возвращением. Поэтому, если цвет окружающей среды интерес должен быть использован в месте, где прозрачность канала имеет важное значение, вы должны использовать IVsUIShell5.GetThemedColor вместо IVsUIShell2::GetVSSysColorEx, как описано позже в этой теме.

##### <a name="from-managed-code"></a>Из управляемого кода
 Доступ к службе VSColor через родной код довольно прост. Однако, если вы работаете через управляемый код, определить, как использовать службу, может быть сложно. Имея это в виду, вот фрагмент кода C', демонстрирующий этот процесс:

```
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

 Если вы работаете в Visual Basic, используйте:

```
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>Из UI WPF
 Вы можете связываться с цветами Visual Studio через значения, экспортированные в ResourceDictionary приложения. Ниже приведен пример использования ресурсов из цветовой таблицы, а также привязки к данным шрифта среды в XAML.

```
<Style TargetType="{x:Type Button}">
    <Setter Property="TextBlock.FontFamily"
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
    <Setter Property="TextBlock.FontSize"
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />
    <Setter Property="Background"
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />
</Style>
```

#### <a name="helper-classes-and-methods-for-managed-code"></a>Классы и методы помощи для управляемого кода
 Для управляемого кода библиотека управляемых пакетов оболочки (Microsoft.VisualStudio.Shell.12.0.dll) содержит несколько классов помощников, облегчающих использование тематических цветов.

 Методы помощи в классе **Microsoft.VisualStudio.Shell.VsColors** в MPF включают **GetThemedGDIColor()** и **GetThemedWPFColor()**. Эти методы помощи возвращают цветовое значение записи темы как System.Drawing.Color или System.Windows.Media.Color, которые будут использоваться в WinForms или WPF UI.

```
IVsUIShell5 shell5;
Button button = new Button();
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);

/// <summary>
/// Gets a System.Drawing.Color value from the current theme for the given color key.
/// </summary>
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>
/// <param name="themeResourceKey">The key to find the color for.</param>
/// <returns>The current theme's value of the named color.</returns>
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);

   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}

private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Guid category = themeResourceKey.Category;
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)
   {
      colorType = __THEMEDCOLORTYPE.TCT_Background;
   }

   // This call will throw an exception if the color is not found
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);
   return BitConverter.GetBytes(rgbaColor);
}
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);

    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}

```

 Класс также может быть использован для получения идентификаторов VSCOLOR для данного цветного ресурса WPF или наоборот.

```
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

 Методы класса **VsColors** запросают службу VSColor, чтобы вернуть цветовое значение каждый раз, когда они вызываются. Чтобы получить цветовое значение, как **System.Drawing.Color**, альтернативой с лучшей производительностью является вместо этого использовать методы **Microsoft.VisualStudio.PlatformUI.VSThemeColor** класса, который кэширует цветовые значения, полученные от службы VSColor. Класс подписывается внутренне, чтобы оболочки событий вещательных сообщений, и отбрасывает кэшированное значение, когда событие изменения темы происходит. Кроме того, класс предоставляет . NET-дружественное мероприятие, чтобы подписаться на тематические изменения. Используйте событие **ThemeChanged,** чтобы добавить новый обработчик, и используйте метод **GetThemedColor()** для получения значений цвета для **ThemeResourceKeys** интереса. Пример кода может выглядеть следующим образом:

```
public MyWindowPanel()
{
    InitializeComponent();

    // Subscribe to theme changes events so we can refresh the colors
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;

    RefreshColors();
}

private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)
{
    RefreshColors();

    // Also post a message to all the children so they can apply the current theme appropriately
    foreach (System.Windows.Forms.Control child in this.Controls)
    {
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);
    }
}

private void RefreshColors()
{
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);
}

protected override void Dispose(bool disposing)
{
    if (disposing)
    {
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;
        base.Dispose(disposing);}
}
```

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a>Выбор цветов высокого контраста

### <a name="overview"></a>Обзор
 Windows использует несколько высококонтрастных тем системного уровня, которые увеличивают цветовую контрастность текста, фона и изображений, делая элементы более отчетливыми на экране. По причинам доступности важно, чтобы элементы интерфейса Visual Studio правильно реагировали при переходе пользователей на тему High Contrast.

 Только горстка цвета системы могут быть использованы для высокой контрастности тем. При выборе названий цвета системы помните следующие советы:

1. **Выберите системные цвета, которые имеют то же семантическое значение,** что и элемент, который вы окрашиваете. Например, если вы выбираете высококонтрастный цвет для текста в окне, используйте WindowText, а не ControlText.

2. **Выберите передний план / фон пары** вместе, или вы не будете уверены, что ваш выбор цвета будет работать во всех темах высокого контраста.

3. **Определите, какие части вашего uI являются наиболее важными, и убедитесь, что области содержимого будут выделяться.** Вы потеряете много деталей, что тонкие различия в цветном оттенке, как правило, различают, так что использование сильных цветов границы является общим для определения содержания областях, потому что Есть нет цветовых вариантов для различных областей содержания.

### <a name="system-color-set"></a>Набор цветов системы
 Таблица на [WPF Team Blog: SystemColors Reference](https://devblogs.microsoft.com/wpf/systemcolors-reference/) указывает полный набор названий цвета системы и соответствующие оттенки, отображаемые в каждой теме.

 При применении этого ограниченного набора цветов к вашему uI, *ожидается, что вы потеряете тонкие детали, которые присутствовали в "нормальных" темах.* Вот пример uI с тонкими серыми цветами, которые используются для различения областей в окне инструмента. При паре с тем же окном, отображаемым в режиме High Contrast, вы можете видеть, что все фоны имеют один и тот же оттенок, а границы этих областей указаны только границами:

 ![Окно "Свойства"](../../extensibility/ux-guidelines/media/030303-a-propertieswindow.png "030303-a_PropertiesWindow")

 **Пример того, как тонкие детали теряются, когда в высокой контрастности**

#### <a name="choosing-text-colors-in-an-editor"></a>Выбор цветов текста в редакторе
 Цветной текст используется в редакторе или на поверхности дизайна для обозначения смысла, например, для легкой идентификации групп похожих элементов. В теме высокого контраста, однако, вы не имеете способность продифференцировать между больше чем 3 цветами текста. WindowText, GrayText и HotTrackText являются единственными цветами, доступными на поверхностях WindowBackground. Так как вы не можете использовать более трех цветов, тщательно выберите наиболее важные различия, которые вы хотите отобразить, когда в режиме высокой контрастности.

 Оттенки для каждого из имен маркеров, разрешенные на поверхности редактора, по мере их появления в каждой теме High Contrast:

 ![Сравнение редактора высокой контрастности](../../extensibility/ux-guidelines/media/030303-b-hceditorcomparison.png "030303-b_HCEditorComparison")

 **Сравнение редактора высокой контрастности**

 Примеры поверхности редактора в голубой теме:

 ![Редактор в "Голубой" теме](../../extensibility/ux-guidelines/media/030303-c-editorblue.png "030303-c_EditorBlue")

 **Редактор в "Голубой" теме**

 ![Редактор в "Высококонтрастной" теме](../../extensibility/ux-guidelines/media/030303-d-editorhc1.png "030303-d_EditorHC1")

 **Редактор в теме высококонтрастной #1**

### <a name="usage-patterns"></a>Варианты использования
 Многие общие элементы uI уже имеют высококонтрастные цвета. Вы можете ссылаться на эти шаблоны использования при выборе собственных названий цвета системы, так что элементы uI согласуются с аналогичными компонентами.

|Цвет системы|Использование|
|------------------|-----------|
|ActiveCaption|- Активный IDE и рафированные пуговицы окна глифы на нависнуть и нажмите<br />- Фон заголовка бар для IDE и рафированные окна<br />- Фон бара состояния по умолчанию|
|ActiveCaptionText|- Активный IDE и рафированные окна для переднего плана титульного бара (текст и глифы)<br />- Фон и граница активных кнопок окна на нависнуть и нажать|
|Control|- Combo box, список выпадающих данных, а также поиск управления по умолчанию и отключен фон, в том числе кнопка выпадения<br />- Док целевой кнопки фон<br />- Фон панели команды<br />- Фон окна инструмента|
|ControlDark|- IDE фон<br />- Меню и командные бары сепараторов<br />- Граница панели команды<br />- Меню тени<br />- Инструмент окно вкладке по умолчанию и нависать границы и сепаратор<br />- Документ хорошо переполнения кнопки фона<br />- Док цель глиф границы|
|ControlDarkDark|- Нефокусированное выбранное окно вкладки документа|
|ControlLight|- Граница вкладок автоматической скрытия<br />- Комбо-коробка и выпадающий список границы<br />- Док целевой фон и границы|
|ControlLight|- Выбранная, сфокусированная временная граница|
|ControlText|- Комбо-коробка и выпадение вниз список глиф<br />- Невыбранный текст вкладки окна инструмента|
|СерыйТекст|- Combo поле и выпадающий список отключен границы, выпадающий глиф, текст, и текст элемента меню<br />- Текст меню для инвалидов<br />- Текст заголовка заголовка управления поиском 'поиск'<br />- Сепаратор секции управления поиском|
|Выделение|- Все нависания и нажата фоны и границы, за исключением комбо окно dropdown кнопки фона и документ хорошо переполнения кнопки границы<br />- Выбранные фоны элементов|
|HighlightText|- Все парят и нажаты на предтечи (текст и глифы)<br />- Фокусированное окно инструмента и управление окном оконного окна вкладки документа<br />- Целенаправленная граница заголовка окна инструмента<br />- Фокусированный, выбранный предварительный передний план вкладки<br />- Документ хорошо переполнения кнопки границы на нависнуть и нажмите<br />- Выбранная граница значка|
|HotTrack|- Прокрутка большого пальца фон и границы на пресс<br />- Прокрутка стрелка глиф на пресс|
|Неактивные caption|- Неактивные IDE и рафированные флоговисы на нависливом<br />- Фон заголовка бар для IDE и рафированные окна<br />- Фон управления поиском отключений|
|НеактивныйcaptionкИТекст|- Неактивный IDE и рафированные окна название бар передний план (текст и глифы)<br />- Неактивные кнопки окна фон и граница на нависнуть<br />- Нефокусированный фон окна инструмента и граница<br />- Отключенный поиск управления передний план|
|Меню|- Предпосылки меню выпадения<br />- Проверенный и отключенный фон чековой отметки|
|MenuText|- Граница меню выпадения<br />- Проверка чековых марок<br />- Меню глифов<br />- Выпадающий текст меню<br />- Выбранная граница значка|
|Полоса прокрутки|- Прокрутка и прокрутки стрелка фон, все состояния|
|Окно|- Фон вкладки автоматической скрытия<br />- Меню бар и фон командной полки<br />- Нефокусированный или невыбранный фон вкладки окна документа и граница документа, как для открытых, так и для предварительных вкладок<br />- Нефокусированный фон заголовка заголовок окна инструмента<br />- Фон вкладки окна инструмента, как выбранный, так и невыбранный|
|Оконная frame|- Граница IDE|
|WindowText|- Авто-скрыть вкладку передний план<br />- Выбранный инструмент окно вкладке переднем плане<br />- Нефокусированная вкладка окна документа и нефокусированный или невыбранный предварительный передний план вкладки<br />- Вид дерева на передний план и нависает над невыбранным глифом<br />- Выбранная граница окна инструмента выбрана граница вкладки<br />- Прокрутка большого пальца фон, граница, и глиф|

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a>Разоблачение цветов для конечных пользователей

### <a name="overview"></a>Обзор
 Иногда вы хотите разрешить конечному пользователю настроить пользовательский интерфейс, например, когда вы создаете редактор кода или поверхность дизайна. Наиболее распространенным способом сделать это является использование **инструменты > параметры** диалога. Если у вас нет узкоспециализированного пользовательского системы, требующего специального контроля, самый простой способ представить настройку — через страницу **шрифтов и цветов** в разделе **«Окружающая среда»** диалога. Для каждого элемента, который вы предоставляете для настройки, пользователь может изменить цвет переднего плана, цвет фона или и то, и другое.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Создание VSPackage для настраиваемых цветов
 VSPackage может управлять шрифтами и цветами через пользовательские категории и отображать элементы на странице свойств шрифтов и цветов. При использовании этого механизма VSPackages должен реализовать интерфейс [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) и связанные с ним интерфейсы.

 В принципе, этот механизм может быть использован для изменения всех существующих элементов отображения и категорий, которые их содержат. Однако он не должен использоваться для изменения категории текстовый редактор или элементов отображения. Для получения дополнительной информации о категории текстовый редактор, [см.](https://msdn.microsoft.com/library/bb165065.aspx)

 Для реализации пользовательских категорий или элементов отображения VSPackage должен:

- **Создание или определение категорий в реестре.** Реализация страницы свойства шрифтов и цветов IDE использует эту информацию для правильного запроса **службы,** поддерживающей заданную категорию.

- **Создание или определение групп в реестре (необязательно).** Возможно, было бы полезно определить группу, которая представляет собой объединение двух или более категорий. Если группа определена, IDE автоматически объединяет подкатегории и распределяет элементы отображения внутри группы.

- **Осуществлять поддержку IDE.**

- **Обработка шрифта и изменения цвета.**

#### <a name="to-create-or-identify-categories"></a>Создание или определение категорий
 Постройте специальный тип входа в реестр категорий в\\ соответствии с\>«HKLM»SOFTWARE»Microsoft «Visual Studio<Visual Studio версии »FontAndColors\\<категория.\> \<Категория> — нелокализованное название категории.

 Заполнить реестр двумя значениями:

|Имя|Тип|Данные |Описание|
|----------|----------|----------|-----------------|
|Категория|REG_SZ|GUID|GUID, созданный для определения категории|
|Пакет|REG_SZ|GUID|GUID службы VSPackage, поддерживающей категорию|

 Услуга, указанная в реестре, должна обеспечить реализацию [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) для соответствующей категории.

#### <a name="to-create-or-identify-groups"></a>Создание или определение групп
 Постройте специальный тип входа в реестр категорий в\\ соответствии с\>«HKLM»SOFTWARE»Microsoft «Visual Studio<Visual Studio версии »FontAndColors\\<группой.\> \<группа> является нелокализованным названием группы.

 Заполнить реестр двумя значениями:

|Имя|Тип|Данные |Описание|
|----------|----------|----------|-----------------|
|Категория|REG_SZ|GUID|GUID, созданный для определения категории|
|Пакет|REG_SZ|GUID|GUID службы VSPackage, поддерживающей категорию|

 Услуга, указанная в реестре, должна обеспечить реализацию **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** для соответствующей группы.

 ![IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a-fontandcolorgroup.png "0304-a_FontAndColorGroup")

### <a name="to-implement-ide-support"></a>Для реализации поддержки IDE
 Реализация [GetObject](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), который возвращает либо [интерфейс IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) или **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** интерфейс для IDE для каждой категории или группы GUID поставляется.

 Для каждой категории, которая поддерживается, VSPackage реализует отдельный экземпляр интерфейса [IVsFontAndColorDefaults.](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)

 Методы, реализованные с помощью [IVsFontAndColorDefaults,](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) должны обеспечить IDE:

- Списки элементов отображения в категории

- Локальные имена для элементов отображения

- Отображение информации для каждого участника категории

  **ПРИМЕЧАНИЕ:** Каждая категория должна содержать по крайней мере один элемент отображения.

  IDE использует интерфейс **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** для определения объединения нескольких категорий.

  Его реализация обеспечивает IDE:

- Список категорий, вкоторыехающие данную группу

- Доступ к экземплярам [IVsFontAndColorDefaults,](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) поддерживающим каждую категорию в группе

- Локализованные названия групп

#### <a name="updating-the-ide"></a>Обновление IDE
 IDE кэширует информацию о настройках шрифта и цвета. Поэтому после любой модификации конфигурации шрифта IDE и цвета, обеспечение того, чтобы кэш был в актуальном состоянии, является наилучшей практикой.

 Обновление кэша осуществляется через интерфейс [IvsFontAndCacheManager](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) и может выполняться глобально или только на отдельных элементах.

### <a name="handling-font-and-color-changes"></a>Обработка шрифта и изменения цвета
 Чтобы должным образом поддержать окраску текста, которую отображает VSPackage, служба окраски, поддерживающая VSPackage, должна реагировать на изменения, внесенные пользователем через страницу свойств шрифтов и цветов.

 Для этого VSPackage должен:

- **обрабатывать события, генерируемые IDE,** реализуя интерфейс [IVsFontAndColorEvents.](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) IDE вызывает соответствующий метод после пользовательских изменений страницы шрифтов и цветов. Например, он вызывает метод [OnFontChanged,](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) если выбран новый шрифт.

  **Или**

- **опрос IDE для изменений**. Это можно сделать с помощью системного интерфейса [IVsFontAndColorStorage.](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) Хотя в первую очередь для поддержки настойчивости, метод [GetItem](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) может получить информацию о шрифте и цвете для элементов отображения. Для получения дополнительной информации о настройках шрифта [Accessing Stored Font and Color Settings](https://msdn.microsoft.com/library/bb166382.aspx)и цвета см.

  **ПРИМЕЧАНИЕ:** Чтобы убедиться, что результаты опроса верны, используйте интерфейс [IVsFontAndColorCacheManager,](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) чтобы определить, необходимы ли флеш кэша и обновление до вызова методов поиска интерфейса [IVsFontAndColorStorage.](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx)

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Регистрация пользовательского шрифта и категории цвета без реализации интерфейсов
 Следующий пример кода демонстрирует, как зарегистрировать пользовательский шрифт и цветовую категорию без реализации интерфейсов:

```xml
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

 **Примечание.**

- "NameID" - идентификатор ресурса локального имени категории в вашем пакете

- "ToolWindowPackage" - пакет GUID

- "Категория" » » » » » » » » » » » » » » » 9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE» является лишь примером, и фактическая стоимость может быть новый GUID, предоставляемый исполнителем.

### <a name="set-the-font-and-color-property-category-guid"></a>Установите категорию свойств шрифта и цвета GUID
 Приведенный ниже пример кода демонстрирует настройку GUID категории.

```cs
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
  IVsTextEditorPropertyContainer spPropContainer;
  Guid GUID_EditPropCategory_View_MasterSettings =
  new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
  hr = spPropCatContainer.GetPropertyCategory(
  ref GUID_EditPropCategory_View_MasterSettings, out spPropContainer);
  if(hr == 0)
  {
    hr = spPropContainer.SetProperty(VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory, catGUID);
    hr = spPropContainer.SetProperty(VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory, catGUID);
  }
}
```
