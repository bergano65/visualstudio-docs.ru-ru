---
title: Цвета и стили для Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 07/31/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: af9522d5773fd74eabcd3b7fce84b7bd56e0cd2a
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="colors-and-styling-for-visual-studio"></a>Цвета и стили для Visual Studio
## <a name="using-color-in-visual-studio"></a>С помощью цвета в Visual Studio
В Visual Studio цвет используется как средство связи не так же, как и оформления. Как минимум используйте цвет и зарезервировать его в ситуациях, где требуется:

-   Связь значения или объединением (например, модификаторы платформы или языка)

-   Привлечь внимание (например, указывающей на изменение состояния)

-   Улучшить читаемость и укажите ориентиры для навигации в пользовательском Интерфейсе

-   Увеличьте desirability

Существует несколько вариантов для назначения цвета для элементов пользовательского интерфейса в Visual Studio. Иногда бывает трудно рисунок, какой параметр вы должны использовать или правильно использовать. В этом разделе помогут вам:

1.  Описание различных служб и систем, используемых для определения цветов в Visual Studio.

2.  Выберите правильный параметр для данного элемента.

3.  Правильно используйте параметр, которую вы выбрали.

> **Примечание:** никогда не следует жестко кодировать hex, RGB или системные цвета для элементов пользовательского интерфейса. Использование служб обеспечивает гибкость в настройке цветовой тон. Кроме того, без этой службы будет невозможно воспользоваться преимуществами возможности переключения темы [службы VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Элементы интерфейса методы для назначения цвета для Visual Studio
Выберите метод, наилучшим образом подходят элементы пользовательского интерфейса.

| Пользовательский Интерфейс | Метод | Что это такое? |
| --- | --- | --- |
| С внедренными или автономный диалоговым окнам. | **Системные цвета** | Системными именами, позволяющие операционной системы определить цвет и внешний вид элементов пользовательского интерфейса, такие как общие элементы управления диалогового окна. |
| У вас есть пользовательский Интерфейс настраиваемой, должны быть согласованы с общей среды VS и иметь элементов пользовательского интерфейса, которые соответствуют категории и семантическое значение общего токенов. | **Стандартные общие цвета** | Существующие имена токенов стандартных цветов для определенных элементов пользовательского интерфейса |
| Необходим для отдельных компонентов или группы функций и общих цвет для аналогичных элементов отсутствует. | **Пользовательские цвета** | Цвет имена токенов, которые относятся к области и не предназначен для совместного использования с другой пользовательский Интерфейс |
| Вы хотите разрешить конечным пользователям изменять пользовательский Интерфейс или содержимого (например, текстовые редакторы или специализированные конструктора windows). | **Настройка конечного пользователя**<br /><br />**(Средства &gt; диалогового окна параметров)** | Параметры, заданные на странице «Шрифты и цвета» **средства &gt; параметры** диалогового окна или специализированные страницы, относящиеся к одной из возможностей пользовательского интерфейса. |

### <a name="visual-studio-themes"></a>Тем Visual Studio
Visual Studio функции три разных цветовых тем: светлую, темную или синюю. Он также определяет режим высокой контрастности, который используется во всей системе цветовой темы, предназначены для специальных возможностей.

Пользователям будет предложено выбрать тему при их первом использовании Visual Studio и способны переключаться темы позже, перейдя к **средства &gt; параметры &gt; среды &gt; Общие** и выбрать новую тему из Раскрывающееся меню «Цветовая тема».

Пользователи также могут использовать панель управления для переключения их всей системы в один из нескольких тем высокой контрастности. Если пользователь выбирает тему с высокой контрастностью, затем Выбор цвета темы Visual Studio больше не влияет на цветов в Visual Studio, несмотря на то, что любое изменение темы сохраняются для, когда пользователь выходит из режима высокой контрастности. Дополнительные сведения о режиме высокой контрастности см. в разделе [Выбор вступили в силу](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Служба VSColor
Visual Studio предоставляет доступ к службе цвет среде, известных как VSColor службы, которое позволяет привязать значения цвета элементов пользовательского интерфейса для именованного запись, содержащая значения цвета для каждой темы Visual Studio. Это гарантирует, что цвета автоматически изменится в соответствии с текущей выбранной пользователем темы или системных режима высокой контрастности. Использование службы означает, что реализация все изменения цвета связанные темы обрабатывается в одном месте и при использовании стандартные общие цвета из службы пользовательского интерфейса автоматически отражают новые темы в будущих версиях Visual Studio.

### <a name="implementation"></a>Реализация
Исходный код Visual Studio включает несколько файлов определения пакета, содержащих списки имен токенов и соответствующих цветовых значений для каждой темы. Служба цвет считывает VSColors, определенные в этих файлах определений пакетов. Эти цвета ссылаются на языке XAML или в коде, а затем загружаются через `IVsUIShell5.GetThemedColor` метода или DynamicResource сопоставление.

### <a name="system-colors"></a>Системные цвета
Стандартные элементы управления ссылаться на системные цвета по умолчанию. Если требуется использовать системные цвета, как и при создании внедренного или на отдельном диалоговом пользовательского интерфейса не нужно выполнять никаких действий.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Стандартные общие цвета в службе VSColor
Свои элементы интерфейса должны отражать общей среды Visual Studio. Используя стандартные общие цвета, которые подходят для компонентов пользовательского интерфейса, которые вы разрабатываете, убедитесь, что интерфейс согласуется с другими интерфейсами Visual Studio и что цветов будут обновляться автоматически при добавлении или обновлении темы.

Прежде чем использовать стандартные общие цвета, убедитесь, что понимаете, как правильно использовать. Стандартные общие цвета неправильное использование может привести к несогласованной, утомительным или сбивающим с толку функционирования для пользователей.

### <a name="user-customizable-colors"></a>Настраиваемые пользователем цвета
См.: [предоставление цвета для конечных пользователей](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

В некоторых случаях требуется разрешить конечным пользователям настраивать пользовательский Интерфейс, как и при создании редактора кода или конструктора. Настраиваемые компоненты пользовательского интерфейса можно найти на **шрифты и цвета** раздел **средства &gt; параметры** диалоговое окно, где пользователям можно изменить цвет и цвет фона.

![Средства &gt; диалогового окна параметров](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301 a_ToolsOptionsDialog")<br />Средства &gt; диалогового окна параметров

##  <a name="BKMK_TheVSColorService"></a> Служба VSColor
Visual Studio предоставляет службе цвета среды, также называемое VSColor службы или службы цвет оболочки. Эта служба позволяет привязать значения цвета элементов пользовательского интерфейса в набор, содержащий цветов для каждой темы имя значение цвета. VSColor службы должен использоваться для всех элементов пользовательского интерфейса, чтобы цвета автоматически изменяются в соответствии с текущей темой, выбранные пользователем, а также, чтобы пользовательский Интерфейс привязан к службе цвета среды будут интегрироваться с новой темы в будущих версиях Visual Studio.

### <a name="how-the-service-works"></a>Как работает служба
Службы цвета среды считывает VSColors, определенный в .pkgdef для компонентов пользовательского интерфейса. Эти VSColors затем имеются ссылки в разметке XAML или кода, загружаются через `IVsUIShell5.GetThemedColor` или `DynamicResource` сопоставления.

![Архитектура службы цвета среды](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302 a_EnvironmentColorServiceArchitecture")<br />Архитектура службы цвета среды разработки

### <a name="accessing-the-service"></a>Доступ к службе
Существует несколько способов доступа к службе VSColor в зависимости от того, какие цвета маркеров вы используете и от типа кода.

#### <a name="predefined-environment-colors"></a>Стандартные среды цветов

##### <a name="from-native-code"></a>Из машинного кода
Оболочка предоставляет службу, которая предоставляет доступ к `COLORREF` цветов. Интерфейс службы и является:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

В файле VSShell80.idl перечисления `__VSSYSCOLOREX` имеет константы цвета оболочки. Чтобы использовать его, передайте в качестве значения индекса либо одно из значений из `enum __VSSYSCOLOREX` документированы в MSDN или обычный индекс номер, система Windows API, `GetSysColor`, принимает. Таким образом обратно возвращает RGB-значение цвета, который должен использоваться в качестве второго параметра.

При хранении, пера или кисти новым цветом, необходимо `AdviseBroadcastMessages` (за пределами оболочки Visual Studio) и прослушивать `WM_SYSCOLORCHANGE` и `WM_THEMECHANGED` сообщений.


Доступ к службе цвет в машинном коде, будет осуществить вызов, который выглядит следующим образом:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> **Примечание:** `COLORREF` значения, возвращаемые методом `GetVSSysColorEx()` содержат только R, G, B компонентов цвета темы. Если запись темы использует прозрачность, значение альфа канала удаляется перед возвратом. Поэтому, если цвет среды процент должен использоваться в том месте, где важна канал прозрачности, следует использовать `IVsUIShell5.GetThemedColor` вместо `IVsUIShell2::GetVSSysColorEx`, как описано далее в этом разделе.

##### <a name="from-managed-code"></a>Из управляемого кода
Доступ к службе VSColor машинного кода, достаточно просто. При работе через управляемый код, однако определение того, как использовать службу может быть непростой задачей. С учетом Вот фрагмент кода C# демонстрацию этого процесса.

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

##### <a name="from-wpf-ui"></a>Из пользовательского интерфейса WPF
Можно привязать к цветам Visual Studio до значения, экспортированные в приложение `ResourceDictionary`. Ниже приведен пример с использованием ресурсов на основе таблицы цветов, а также привязка к данным шрифт среды в XAML.

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

#### <a name="helper-classes-and-methods-for-managed-code"></a>Вспомогательные классы и методы для управляемого кода
Для управляемого кода, библиотека Managed Package Framework оболочки (`Microsoft.VisualStudio.Shell.12.0.dll`) содержит несколько вспомогательных классов использует тематические цвета.

Вспомогательные методы в `Microsoft.VisualStudio.Shell.VsColors` класс в MPF включать `GetThemedGDIColor()` и `GetThemedWPFColor()`. Эти вспомогательные методы возвращают значение цвета темы записи как `System.Drawing.Color` или `System.Windows.Media.Color`, для использования в WinForms или пользовательского интерфейса WPF.

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

Класс может также использоваться для получения идентификаторов VSCOLOR указанного WPF цвета ресурсов ключа, или наоборот.

```
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Методы `VsColors` класс запроса VSColor службы для возврата значения цвета при каждом их вызове. Чтобы получить значение цвета, как `System.Drawing.Color`, альтернативой с точки зрения производительности является вместо этого использовать методы `Microsoft.VisualStudio.PlatformUI.VSThemeColor` класс, который кэширует значения цвета, полученного от службы VSColor. Класс внутренне подписывается на события широковещательных сообщений оболочки и отменяет кэшированное значение, когда происходит событие изменения темы. Кроме того, этот класс предоставляет. NET-friendly событий для подписки на изменения темы. Используйте `ThemeChanged` событий, чтобы добавить новый обработчик и использовать `GetThemedColor()` значения для получения цвет `ThemeResourceKeys` интерес. Пример кода может выглядеть следующим образом:

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

##  <a name="BKMK_ChoosingHighContrastColors"></a> Выбор цвета высокой контрастности

### <a name="overview"></a>Обзор
Windows использует несколько тем системного уровня высокой контрастности, увеличьте контрастность цвет текста, цвет фона и изображений, делая элементов более отчетливым на экране. Для поддержки специальных возможностей очень важно, что элементы интерфейса Visual Studio правильно ответить, когда пользователи переходят высококонтрастную тему.

Для режима высокой контрастности темы можно лишь небольшое количество системных цветов. При выборе системы имена цветов, помните следующие рекомендации:

1.  **Выберите системных цветов, которые имеют одинаковое значение семантики** с элементом, выделение цветом. Например при выборе высокой контрастности цвет для текста в окне используйте WindowText и не ControlText.

2.  **Выбрать пары переднего плана и фона** вместе или не быть уверены, выбранный цвет будет работать на всех тем высокой контрастности.

3.  **Определить, какие части пользовательского интерфейса самые важные и убедитесь, что области содержимого будет выделяться.** Поэтому использование цвета границы строгого является стандартным для определения области содержимого, поскольку существуют варианты не цветов для различных областей содержимого множество подробных сведений, который обычно будет отличить небольшие отличия в цветового тона, будут потеряны.

### <a name="system-color-set"></a>Набор системных цветов
Таблицы на [блог команды разработчиков WPF: ссылка SystemColors](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) указывает полный набор имена системных цветов и соответствующий тона, отображаемых в каждой темы.

При применении это ограниченный набор цветов к пользовательскому Интерфейсу *ожидается, будут потеряны слабая сведения, которые присутствовали в «normal» темы*. Ниже приведен пример пользовательского интерфейса с слабая серым цветом, которые используются для различения областей в окно инструментов. При совместном использовании то же окно, которое отображается в режиме высокой контрастности, вы увидите, что фон тот же оттенок и границы этих областей обозначаются границы сама по себе:

![Примером как небольшие сведения могут быть потеряны при высокой контрастности](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 a_PropertiesWindow")<br />Примером как небольшие сведения могут быть потеряны при высокой контрастности

#### <a name="choosing-text-colors-in-an-editor"></a>Выбор цвета текста в редакторе
Цветом текста используется в редакторе или в области конструктора для указания значения, такие как разрешение для упрощения идентификации групп схожих элементов. В тему с высокой контрастностью Однако у вас может различать более трех цветов текста. WindowText, GrayText и HotTrackText являются только цветов, доступных на поверхности WindowBackground. Поскольку нет возможности использовать более трех цветов, тщательно выберите наиболее важные отличия, которые нужно отобразить в режиме высокой контрастности.

Оттенки каждого имена токенов, допустимое в рабочей области редактора, как они отображаются в каждом высококонтрастную тему:

![Сравнение редактора высокой контрастности](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 b_HCEditorComparison")<br />Сравнение редактора высокой контрастности

Примеры поверхности редактор в "голубой" теме.

![Редактор в "голубой" теме](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 c_EditorBlue")<br />Редактор в "Голубой" теме

![Редактор в теме высокой контрастности #1](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 d_EditorHC1")<br />Редактор в теме высокой контрастности #1

### <a name="usage-patterns"></a>Использование шаблонов
Многие стандартные элементы пользовательского интерфейса, уже определено Высокая контрастность цветов. Эти шаблоны использования можно ссылаться при выборе собственной системы имена цветов, таким образом, согласованные с аналогичными компонентами элементы пользовательского интерфейса.

| Системный цвет | Использование |
| --- | --- |
| ActiveCaption | -Active IDE и rafted окна глифы кнопка при наведении указателя мыши и нажмите клавишу<br />— Название фона панели для интегрированной среды разработки и rafted windows<br />-По умолчанию фон строки состояния |
| ActiveCaptionText | -Active интегрированной среды разработки и rafted windows для заголовка панели передний план (текст и глифы)<br />-Фона и границы активного окна кнопки при наведении указателя мыши и нажмите клавишу |
| Элемент управления | -Поле со списком, раскрывающегося списка и поиск элемента управления по умолчанию и отключить фон, включая кнопку раскрывающегося списка<br />-Цвет фона кнопки целевой закрепления<br />-Фона панели команда<br />-Фон окна средство |
| ControlDark | -Фон IDE<br />-Панель разделители меню и команд<br />-Граница панели команда<br />-Shadows меню<br />-Средство разделитель и границы окна вкладка по умолчанию и при наведении курсора мыши<br />-Документов также цвет фона для кнопки переполнения<br />-Границы глифа целевой закрепления |
| ControlDarkDark |-Окно вкладки без фокуса ввода, выбранный документ |
| ControlLight |-Граница вкладки автоматического скрытия<br />-Границы списка поля со списком поле и раскрывающийся список<br />-Закрепить целевой фона и границ |
| ControlLightLight | -Установлен, имеющего фокус временной границы |
| ControlText | -Глиф список поля со списком поле и раскрывающийся список<br />-Текст вкладки окна, не выбранные средство |
| GrayText |-Поле со списком и раскрывающегося списка отключены границы, глиф раскрывающийся список, текст и текст пункта меню<br />— Текст отключенное меню<br />-Текст заголовка поиска элемент управления «параметры поиска»<br />-Разделитель секций поиска элемент управления |
| Выделение | -Все при наведении указателя мыши и нажатой цвет фона и границы, за исключением того, поле со списком поле разворачивающуюся кнопку документ и фона хорошо переполнения граница кнопки<br />-Фон выбранного элемента |
| HighlightText | -Все при наведении указателя мыши и нажатой foregrounds (текст и глифы)<br />-Конкретное средство документом и окном вкладки окна управления переднего плана<br />-Граница заголовка окна инструмента конкретное окно<br />-Фокус, выбранный временной вкладке переднего плана<br />-Граница кнопки переполнения хорошо документа при наведении указателя мыши и нажмите клавишу<br />-Границы выбранный значок|
| HotTrack | -Полоса прокрутки thumb фона и границ на машине<br />-Полосы прокрутки глиф нажмите клавишу со стрелкой |
| InactiveCaption | -Неактивные IDE и rafted окна глифы кнопка при наведении курсора мыши<br />— Название фона панели для интегрированной среды разработки и rafted windows<br />— Фон элемента управления отключенное поиска |
| InactiveCaptionText | -Неактивные IDE и rafted windows заголовка панели передний план (текст и глифы)<br />-Неактивного окна кнопки фона и границ при наведении курсора мыши<br />-Цвет фона кнопки окна инструментов без фокуса ввода и границы<br />-Передний план управления поиска отключено |
| Меню | -Фон раскрывающегося меню<br />-Фон флажка установлен и отключен |
| MenuText | -Границы раскрывающегося меню<br />-Метки<br />-Глифы меню<br />-Текст раскрывающегося меню<br />-Границы выбранный значок |
| Полоса прокрутки | -Прокрутите панель и прокрутка стрелки фон, все состояния |
| Окно | -Вкладка фона автоматического скрытия<br />-Меню полосы, а команда фона Полка<br />-Фон вкладки окна документа без фокуса ввода или невыбранные и границу документа, для открытых и временной вкладок<br />-Фона панели заголовка окна инструмента без фокуса ввода<br />-Фон окна инструментов вкладки, как выбран и не выбрано |
| WindowFrame | -Границы IDE |
| WindowText | -Передний план вкладку автоматического скрытия<br />-Передний план вкладку окна выбранное средство<br />-Вкладка окна документа без фокуса ввода и без фокуса ввода или невыбранные временной вкладке переднего плана<br />-Дереве представления цвет переднего плана и при наведении указателя мыши на глиф невыбранные<br />-Граница выбранная вкладка окна инструментов<br />-Полосы прокрутки thumb фона, границы и глифа |

##  <a name="BKMK_ExposingColorsForEndUsers"></a> Предоставление доступа к цвета для конечных пользователей

### <a name="overview"></a>Обзор
Иногда может потребоваться разрешить конечным пользователям настраивать пользовательский Интерфейс, как и при создании редактора кода или конструктора. Наиболее распространенный способ сделать это — с помощью **средства &gt; параметры** диалогового окна. Если не имеют очень специализированную пользовательский Интерфейс, который требует специальных элементов управления, самый простой способ настройки представления является через **шрифты и цвета** страницы в пределах **среды** диалогового окна. Для каждого элемента, который предоставить для настройки пользователя можно изменить цвет и цвет фона.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Создание VSPackage для настраиваемых цветов
Пакет VSPackage можно управлять шрифтов и цветов через пользовательские категории и отображения элементов на странице свойств шрифты и цвета. При использовании этого механизма, пакеты VSPackage должны реализовывать [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) интерфейса и его связанных интерфейсов.

В принципе этот механизм может использоваться для изменения всех существующих отображаемые элементы и категории, которые их содержат. Тем не менее он должен использоваться не для изменения текстовый редактор или своих отображаемых элементов. Дополнительные сведения о категории текстового редактора в разделе [шрифт и цвет Обзор](../font-and-color-overview.md).

Чтобы реализовать пользовательские категории или отображать элементы, пакет VSPackage должен удовлетворять следующим требованиям:

-   **Создайте или определите категории в реестре.** Реализация IDE **шрифты и цвета** страница свойств использует эти сведения для запроса правильно для службы, поддерживающей данной категории.

-   **Создайте или определите группы в реестре (необязательно).** Может быть полезно для определения группы, представляющий объединение двух или более категорий. При определении группы, интегрированной среды разработки автоматически выполняет слияние подкатегории и распространяет отображаемые элементы в пределах группы.

-   **Реализация поддержки IDE.**

-   **Обрабатывать изменения цвета и шрифта.**

#### <a name="to-create-or-identify-categories"></a>Для создания и определения категорий
Создать специальный тип категории запись реестра `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` где `<Category>` нелокализованное имя категории.

Добавить в реестр с двумя значениями:

| name | Тип | Данные | Описание |
| --- | --- | --- | --- |
| Категория | REG_SZ | Идентификатор GUID | Идентификатор GUID, созданный для определения категории |
| Пакет | REG_SZ | Идентификатор GUID | Идентификатор GUID для пакета VSPackage службы, которая поддерживает категории |

 Службы, указанный в разделе реестра необходимо обеспечить реализацию [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) для соответствующей категории.

#### <a name="to-create-or-identify-groups"></a>Для создания и определения групп
Создать специальный тип категории запись реестра `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` где `<group>` нелокализованное имя группы.

Добавить в реестр с двумя значениями:

| name | Тип | Данные | Описание |
|--- | --- | --- | --- |
| Категория | REG_SZ | Идентификатор GUID | Идентификатор GUID, созданный для определения категории |
| Пакет | REG_SZ | Идентификатор GUID | Идентификатор GUID для пакета VSPackage службы, которая поддерживает категории |

Службы, указанный в разделе реестра необходимо обеспечить реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> для соответствующей группы.

![Implementation of IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Реализация `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Чтобы обеспечить поддержку интегрированной среды разработки
Реализуйте [GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), которое возвращает либо [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) интерфейса или <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> интерфейс IDE для каждой категории или группы кодом GUID.

Для каждой категории, он поддерживает, VSPackage реализует отдельный экземпляр [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) интерфейса.

Методы реализуется с помощью [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) необходимо предоставить среду IDE:

-   Списки элементов в категории

-   Локализуемые имен для отображения элементов

-   Отображаемые сведения для каждого элемента категории

 > **Примечание:** каждой категории должен содержать хотя бы один элемент для отображения.

Интегрированная среда разработки использует <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> интерфейс, чтобы определить объединение несколько категорий.

Его реализация предоставляет интегрированную среду разработки с помощью:

-   Список категорий, которые составляют заданной группы

-   Доступ к экземплярам [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) поддержки каждой категории в группе

-   Имена групп локализуемые

#### <a name="updating-the-ide"></a>Обновление интегрированной среды разработки
IDE кэширует сведения о параметрах шрифтов и цветов. Таким образом после внесения изменений конфигурации IDE шрифта и цвета, чтобы убедиться в актуальном состоянии кэша является лучшим способом.

Обновление кэша выполняется с помощью [IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) интерфейс, а также может быть выполнено глобально или только на выбранные элементы.

### <a name="handling-font-and-color-changes"></a>Обработка изменений шрифта и цвета
Для правильной поддержки выделение цветом текста, который отображает VSPackage, выделение цветом служба, поддерживающая VSPackage должен отвечать на инициированной пользователем изменения, внесенные на странице свойств шрифты и цвета.

Чтобы сделать это, пакет VSPackage должен удовлетворять следующим требованиям:

-   **обрабатывать события, вызываемые IDE** путем реализации [IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) интерфейса. IDE вызывает соответствующий метод следующие пользовательские изменения страницы шрифты и цвета. Например, он вызывает [OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) метод, если выбран новый шрифт.

 **OR**

-   **опрос интегрированную среду разработки для изменения**. Это можно сделать с помощью реализовать систему [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) интерфейса. Несмотря на то что в основном для поддержки сохраняемости, [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) метода можно получить сведения о шрифт и цвет для отображения элементов. Дополнительные сведения о параметрах шрифтов и цветов см. в статье MSDN [параметров доступа к хранимых шрифта и](../accessing-stored-font-and-color-settings.md).

> **Примечание:** чтобы гарантировать правильность результатов опроса, используйте [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) интерфейс, чтобы определить необходимость сброса кэша и обновления перед вызовом методов получения [ IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) интерфейса.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Регистрация пользовательского шрифта и цвета категории без реализации интерфейсов
В следующем примере кода показано, как зарегистрировать пользовательский шрифт и цветовые категории без реализации интерфейсов:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Для этого примера кода:
-   `"NameID"` = Идентификатор ресурса имя локализованной категории в пакет
-   `"ToolWindowPackage"` = Идентификатор GUID пакета
-   `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` всего лишь пример и фактическое значение может быть новый идентификатор GUID, предоставленный средством реализации.

### <a name="set-the-font-and-color-property-category-guid"></a>Задать шрифт и цвет свойство GUID категории
В примере кода показано задание GUID категории.

```
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
IVsTextEditorPropertyContainer spPropContainer;
Guid GUID_EditPropCategory_View_MasterSettings =
new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
hr = spPropCatContainer.GetPropertyCategory(
ref GUID_EditPropCategory_View_MasterSettings,
out spPropContainer);
if(hr == 0)
{
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory,
catGUID);
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory,
catGUID);
}
}
```
