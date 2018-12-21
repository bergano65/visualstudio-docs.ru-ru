---
title: Цвета и стили для Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 84ade82822d5481d098fe98408a130ba93f68ee0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725711"
---
# <a name="colors-and-styling-for-visual-studio"></a>Цвета и стили для Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="using-color-in-visual-studio"></a>С помощью цвета в Visual Studio  
 В Visual Studio он используется главным образом в качестве средства коммуникации, не так же, как и оформление. Как минимум используйте цвет и зарезервировать его для ситуаций, где вы хотите:  
  
- Связь значения или объединением (например, платформы или языка модификаторы)  
  
- Привлечение внимания (например, указывающей на изменение состояния)  
  
- Улучшить читаемость и предоставить ориентиров для навигации в пользовательском Интерфейсе  
  
- Увеличить desirability  
  
  Существует несколько вариантов для назначения цветов для элементов пользовательского интерфейса в Visual Studio. Иногда может быть трудно рис out какой вариант вы должны использовать или правильно его использовать. В этом разделе помогут вам:  
  
1. Сведения о различных служб и систем, используемых для определения цветов в Visual Studio.  
  
2. Выберите правильный параметр для данного элемента.  
  
3. Правильно используйте параметр, которую вы выбрали.  
  
   **Важно:** никогда не следует жестко кодировать hex, RGB или системных цветов для элементов пользовательского интерфейса. Использование служб обеспечивает гибкость в настройке hue. Кроме того, без службы, не можно пользоваться преимуществами возможностей Переключение тем [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Элементы интерфейса методы для назначения цвета для Visual Studio  
 Выберите метод, который лучше всего подходит для элементов пользовательского интерфейса.  
  
|Пользовательский Интерфейс|Метод|Что это такое?|  
|-------------|------------|--------------------|  
|С внедренными или автономный диалоговым окнам.|**Системные цвета**|Системными именами, которые позволяют операционной системы определить цвет и внешний вид элементов пользовательского интерфейса, такие как для общих элементов управления диалогового окна.|  
|У вас есть пользовательский Интерфейс, необходимый для согласования с общей среды VS и у вас есть элементы пользовательского интерфейса, соответствующие категории и семантическое значение общих маркеров.|**Стандартные общие цвета**|Существующие имена токенов предопределенного цвета для конкретных элементов пользовательского интерфейса|  
|Вы располагаете соглашением отдельных компонентов или набор компонентов и общий цвет для аналогичных элементов отсутствует.|**Пользовательские цвета**|Цвет маркера имена, которые относятся к области и не предназначен для совместного использования с другой пользовательский Интерфейс|  
|Вы хотите разрешить конечным пользователям изменять пользовательский Интерфейс или содержимое (например, для текстовых редакторов или специализированные конструктора windows).|**Настройка конечного пользователя**<br /><br /> **(Сервис > Параметры диалогового окна)**|Параметры, определенные на странице «Шрифты и цвета» **Сервис > Параметры** диалогового окна или специализированные страницы, относящиеся к одной возможности пользовательского интерфейса.|  
 
  
### <a name="visual-studio-themes"></a>Тем Visual Studio  
 Visual Studio содержит три разных цветовых тем: светлую, темную или синюю. Она также обнаруживает режим высокой контрастности, который используется во всей системе цветовую схему для специальных возможностей.  
  
 Пользователям будет предложено выбрать тему при их первом использовании Visual Studio и могут переключать темы позже, выбрав **Сервис > Параметры > среда > Общие** и выбрав новую тему из раскрывающегося списка «Цветовая тема».  
  
 Пользователи также могут использовать панель управления для переключения их всей системы в один из нескольких тем высокой контрастности. Если пользователь выбирает тему с высокой контрастностью, затем средство выбора темы цвета Visual Studio больше не влияет на цветов в Visual Studio, несмотря на то, что любое изменение темы сохраняются для, когда пользователь выходит из режима высокой контрастности. Дополнительные сведения о режиме высокой контрастности, см. в разделе [Выбор высокой контрастности цветов](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).  
  
### <a name="the-vscolor-service"></a>VSColor service  
 Visual Studio предоставляет службе цвета среды, известный как VSColor service, который позволяет выполнять привязку значения цвета элементов пользовательского интерфейса для именованную запись, содержащую значения цвета для каждой темы Visual Studio. Это гарантирует, что цвета автоматически изменится в соответствии с текущей выбранной пользователем темы или системных режима высокой контрастности. Использование службы означает, что реализацию всех изменений в связанные темы цвета обрабатывается в одном месте, и если вы используете стандартные общие цвета из службы, пользовательский Интерфейс будет автоматически отражать новые темы в будущих версиях Visual Studio.  
  
### <a name="implementation"></a>Реализация  
 Исходный код Visual Studio включает в себя несколько файлов определения пакета, содержащих списки имена токенов и значений соответствует цвету для каждой темы. Цвет служба считывает VSColors, определенные в этих файлах определений пакетов. Эти цвета ссылки в разметке XAML или в коде, а затем загружаются через **IVsUIShell5.GetThemedColor** метода или сопоставление DynamicResource.  
  
### <a name="system-colors"></a>Системные цвета  
 Стандартные элементы управления, чтобы ссылаться на системные цвета по умолчанию. Если вы хотите использовать системные цвета, например при создании внедренного или на отдельном диалоговом окне пользовательского интерфейса не нужно ничего делать.  
  
### <a name="common-shared-colors-in-the-vscolor-service"></a>Стандартные общие цвета в VSColor service  
 Ваши элементы интерфейса должны отражать всей средой Visual Studio. Повторно используя стандартные общие цвета, которые подходят для компонентов пользовательского интерфейса, которые вы разрабатываете, убедитесь, что интерфейс согласуется с другими интерфейсами Visual Studio и что цвета будут обновляться автоматически при добавлении или обновлении тем.  
  
 Прежде чем использовать стандартные общие цвета, убедитесь, что вы знаете, как правильно их использовать. Неправильное использование стандартные общие цвета может привести к несогласованные, неудобства или путаницу функционирования для пользователей.  
  
### <a name="user-customizable-colors"></a>Настраиваемые пользователем цвета  
 См.: [предоставление цвета для конечных пользователей](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)  
  
 В некоторых случаях требуется разрешить конечным пользователям изменять пользовательский Интерфейс, например при создании кода редактора или конструктора. Настраиваемые компоненты пользовательского интерфейса можно найти в **шрифты и цвета** раздел **Сервис > Параметры** диалоговое окно, где пользователи могут изменить цвет переднего плана и цвет фона.  
  
 ![Средства &#62; диалоговое окно параметров в Visual Studio](../../extensibility/ux-guidelines/media/0301-a-toolsoptionsdialog.png "0301 a_ToolsOptionsDialog")  
  
 **Сервис > Параметры диалогового окна**  
  
 
##  <a name="BKMK_TheVSColorService"></a> VSColor Service  
 Visual Studio предоставляет службе цвета среды, также называется VSColor service или службы цветов оболочки. Эта служба позволяет привязать значения цвета элементов пользовательского интерфейса в набор, содержащий цвета для каждой темы имя значение цвета. VSColor service необходимо использовать для всех элементов пользовательского интерфейса, так что цветов автоматически изменяются в соответствии с текущей темой, выбранные пользователем и таким образом, чтобы пользовательский Интерфейс привязан к службе цвета среды будет интегрировано с новой темы в будущих версиях Visual Studio.  
  
### <a name="how-the-service-works"></a>Принцип работы службы  
 Службы цвета среды считывает VSColors, определенных в .pkgdef для компонента пользовательского интерфейса. Эти VSColors указываются в разметке XAML или код, загружаются через **IVsUIShell5.GetThemedColor** или сопоставление DynamicResource.  
  
 ![Архитектура службы цвета среды](../../extensibility/ux-guidelines/media/0302-a-environmentcolorservicearchitecture.png "0302 a_EnvironmentColorServiceArchitecture")  
  
 **Архитектура службы цвета среды**  
  
### <a name="accessing-the-service"></a>Доступ к службе  
 Существует несколько способов доступа VSColor service, в зависимости от того, какого рода цвет маркеров вы используете и какого рода кода у вас есть.  
  
#### <a name="predefined-environment-colors"></a>Цвета стандартные среды  
  
##### <a name="from-native-code"></a>Из машинного кода  
 Оболочка предоставляет службу, которая предоставляет доступ к COLORREF цвета. Интерфейс службы и является:  
  
```  
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)  
```  
  
 В файле vsshell80.IDL, раздел перечисления файле **__VSSYSCOLOREX** имеет константы цвета оболочки. Чтобы использовать его, передайте значение индекса, либо одно из значений из перечисления __VSSYSCOLOREX, описаны в MSDN или обычный индекс номер, который система Windows API, **GetSysColor**, принимает. Это снова возвращает RGB-значение цвета, который должен использоваться в качестве второго параметра.  
  
 Если хранить пера или кисти с новый цвет, необходимо AdviseBroadcastMessages (за пределами оболочки Visual Studio) и прослушивание сообщений из WM_SYSCOLORCHANGE и WM_THEMECHANGED.  
  
```  
// To access the color service in native code, you'll make a call that resembles this:  
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);  
  
```  
  
 **Примечание:** COLORREF значения, возвращаемые методом **GetVSSysColorEx()** содержат только R, G, B компонентов цвета темы. Если запись Тема используется прозрачность, значение альфа канала удаляется перед возвратом. Таким образом Если нужный цвет среде должен быть используется в том месте, где важна канал прозрачности, следует использовать IVsUIShell5.GetThemedColor вместо IVsUIShell2::GetVSSysColorEx, как описано далее в этом разделе.  
  
##### <a name="from-managed-code"></a>Из управляемого кода  
 Доступ к службе VSColor машинного кода, достаточно просто. При работе через управляемый код, тем не менее, определяет, как использовать службу может быть непростой задачей. С учетом этого Вот фрагмент кода C# демонстрацию этого процесса:  
  
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
  
##### <a name="from-wpf-ui"></a>С помощью пользовательского интерфейса WPF  
 Можно привязать к цветам Visual Studio через значениями, экспортированными в ResourceDictionary приложения. Ниже приведен пример использования ресурсов из таблицы цветов, а также для привязки к данным шрифта среды в XAML.  
  
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
 Для управляемого кода библиотека Managed Package Framework оболочки (Microsoft.VisualStudio.Shell.12.0.dll) содержит несколько вспомогательных классов использует цвета темы.  
  
 Вспомогательные методы в **Microsoft.VisualStudio.Shell.VsColors** включить класс в MPF **GetThemedGDIColor()** и **GetThemedWPFColor()**. Эти вспомогательные методы возвращают значение цвета темы записи как System.Drawing.Color или System.Windows.Media.Color, для использования в Windows Forms или пользовательского интерфейса WPF.  
  
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
  
 Класс также может быть использован для получения VSCOLOR идентификаторы для заданного ключа ресурса цвета WPF, или наоборот.  
  
```  
public static string GetColorBaseKey(int vsSysColor);  
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);  
```  
  
 Методы **VsColors** класс запроса VSColor service, чтобы вернуть значение цвета каждый раз, они вызываются. Чтобы получить значение цвета, как **System.Drawing.Color**, в качестве альтернативы с более высокой производительностью предлагается вместо этого используйте методы класса **Microsoft.VisualStudio.PlatformUI.VSThemeColor** класса, кэширующий значение цвета, полученный из VSColor service. Класс внутренне подписывается на события широковещательных сообщений оболочки и отбрасывает кэшированное значение, когда происходит событие изменения темы. Кроме того, этот класс предоставляет. Событие NET-friendly подписаться на изменения темы. Используйте **ThemeChanged** событие, чтобы добавить новый обработчик и использовать **GetThemedColor()** метод, чтобы получить цвет значений в параметре **ThemeResourceKeys** интерес. Пример кода может выглядеть следующим образом:  
  
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
 Windows использует несколько тем высокой контрастности системного уровня, которые увеличить контрастность текста, фоновые рисунки и изображения, что делает более отчетливым на экране элементы. Для поддержки специальных возможностей очень важно, что элементы интерфейса Visual Studio правильно реагировать, когда пользователи переходят тему с высокой контрастностью.  
  
 Можно использовать лишь небольшое количество системных цветов для тем высокой контрастности. При выборе системы имена цветов, помните следующие советы:  
  
1.  **Выберите системных цветов, которые имеют одинаковое значение семантической** как элемент, который выделение цветом. Например если вы выбираете цвета высокой контрастности для текста в окне, используйте WindowText и не ControlText.  
  
2.  **Выберите пары переднего плана и фона** вместе или не быть уверены в том, что выбранный цвет будет работать во всех темах высокой контрастности.  
  
3.  **Определить, какие части пользовательского интерфейса наиболее важны и убедитесь, что области содержимого будет выделяться.** Вы потеряете много подробных сведений, который обычно будет отличить небольшие отличия в оттенок цвета, поэтому надежный цвета используется общие для определения области содержимого, так как существуют варианты не цвет для различных областей содержимого.  
  
### <a name="system-color-set"></a>Набор цветов для системы  
 Таблицы на [блог группы разработчиков WPF: ссылка SystemColors](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) указывает полный набор названий цветов системы и соответствующие тона, отображаемых в каждой темы.  
  
 При применении это ограниченный набор цветов для пользовательского интерфейса, *предполагается, что вы потеряете тонких моментов, которые присутствовали в «normal» темы*. Ниже приведен пример пользовательского интерфейса с слабая серого цвета, которые используются для отделения области в окне инструментов. При совместном использовании с окно отображается в режиме высокой контрастности, вы увидите, что все фоновые рисунки тот же оттенок и границ в этих областях обозначаются только границы:  
  
 ![Окно "Свойства"](../../extensibility/ux-guidelines/media/030303-a-propertieswindow.png "030303 a_PropertiesWindow")  
  
 **Пример того, как слабая сведения будут удалены при высокой контрастности**  
  
#### <a name="choosing-text-colors-in-an-editor"></a>Выбор цвета текста в редакторе  
 Цветом текст используется в редакторе или в области конструктора для указания значения, например, позволяет легко идентифицировать групп схожих элементов. В теме высокой контрастности тем не менее, у вас возможность различать более трех цветов текста. WindowText, GrayText и HotTrackText являются только цветов, доступных на поверхностях WindowBackground. Так как нет возможности использовать более трех цветов, тщательно выбирайте наиболее важные отличия, которые нужно отобразить в режиме высокой контрастности.  
  
 Тона для каждого из имен токенов, допустимое в рабочей области редактора, как они указаны в каждой теме высокой контрастности:  
  
 ![Сравнение редактора высокой контрастности](../../extensibility/ux-guidelines/media/030303-b-hceditorcomparison.png "030303 b_HCEditorComparison")  
  
 **Сравнение редактора высокой контрастности**  
  
 Примеры в области "редактор" в "голубой" теме:  
  
 ![Редактор в "голубой" теме](../../extensibility/ux-guidelines/media/030303-c-editorblue.png "030303 c_EditorBlue")  
  
 **Редактор в "голубой" теме**  
  
 ![Редактор в "высококонтрастной" теме](../../extensibility/ux-guidelines/media/030303-d-editorhc1.png "030303 d_EditorHC1")  
  
 **Редактор в теме высокой контрастности № 1**  
  
### <a name="usage-patterns"></a>Шаблоны использования  
 Множество общих элементов пользовательского интерфейса уже определено высокой контрастности цветов. Эти шаблоны использования можно ссылаться при выборе собственной системы имена цветов, таким образом, элементы пользовательского интерфейса были согласованы с похожими компонентов.  
  
|Системный цвет|Использование|  
|------------------|-----------|  
|ActiveCaption|-Active интегрированной среды разработки и rafted окно глифы кнопка при наведении указателя мыши и нажмите клавишу<br />-Фона панели заголовка для интегрированной среды разработки и rafted windows<br />-Фона строки состояния по умолчанию|  
|ActiveCaptionText|-Active интегрированной среды разработки и rafted windows заголовок панели цвета переднего плана (текст и глифов)<br />-Фона и границы активного окна кнопок на при наведении указателя мыши и нажмите клавишу|  
|Элемент управления|-Поле со списком, раскрывающийся список и элемент управления по умолчанию и отключено фон поиска, включая кнопку раскрывающегося списка<br />-Фона кнопки целевого объекта закрепления<br />-Фона панели команд<br />-Фон окна средство|  
|ControlDark|-Фон IDE<br />-Разделители панели меню и команды<br />-Граница панели команд<br />-Shadows меню<br />-Средство границы по умолчанию и наведите ее на вкладке окна и разделителя<br />-Документа также цвет фона для кнопки переполнения<br />-Границы глифа целевого закрепления|  
|ControlDarkDark|-Окно вкладки без фокуса ввода, выбранный документ|  
|ControlLight|-Граница вкладки автоматического скрытия<br />-Границы поле со списком поле и выберите в раскрывающемся списке<br />-Закрепление фона целевого объекта и границы|  
|ControlLightLight|-Выбранного фокусом временное граница|  
|ControlText|-Глиф поле со списком поле и выберите в раскрывающемся списке<br />-Текст вкладки окна невыделенного инструментов|  
|GrayText|-Поле со списком и границы списка отключена раскрывающийся список, глифа раскрывающегося списка, текст и текст пункта меню<br />-Текст меню отключен<br />-Текст заголовка для элемента управления «параметры поиска» поиска<br />-Разделитель секций поиск элемента управления|  
|Выделение|-All при наведении указателя мыши и нажата фон и границы, за исключением раскрывающемся поле со списком фона кнопки и документ также overflow границы кнопки<br />-Фон выбранного элемента|  
|HighlightText|-Все при наведении указателя мыши и нажата foregrounds (текст и глифов)<br />-Фокусом средство документом и окном вкладку окна управления переднего плана<br />-Граница панели заголовка окна фокусом инструментов<br />-Фокусом, выбранный временной вкладке переднего плана<br />-Граница кнопки переполнения хорошо документа при наведении указателя мыши и нажмите клавишу<br />-Границы выбранный значок|  
|HotTrack|— Фона бегунка полосы прокрутки и границу на клавишу<br />-Глиф стрелки полосы прокрутки на материалах издательства press|  
|InactiveCaption|-Неактивные интегрированной среды разработки и rafted окно глифы кнопка при наведении курсора мыши<br />-Фона панели заголовка для интегрированной среды разработки и rafted windows<br />— Фон элемента управления отключенное поиска|  
|InactiveCaptionText|-Неактивные интегрированной среды разработки и rafted windows заголовок панели передний план (текст и глифов)<br />-Фон кнопки неактивного окна и граница при наведении курсора мыши<br />-Цвет фона кнопки окна инструмента без фокуса ввода и границы<br />-Переднего плана элемента управления поиска отключено|  
|Меню|-Фон раскрывающегося меню<br />-Checked и отключенный флажок фона|  
|MenuText|-Границы раскрывающегося меню<br />-Проверка меток<br />-Глифы меню<br />-Текст раскрывающегося меню<br />-Границы выбранный значок|  
|Полоса прокрутки|-Scrollbar и полосы прокрутки фона стрелки, все состояния|  
|Окно|Автоматическое скрытие фона вкладки<br />-Меню панели и фона полки команды<br />-Фона вкладки окна документа без фокуса ввода или невыделенного и границы документа для вкладки как открытые, так и временное<br />-Фон панели заголовка окна без фокуса ввода инструментов<br />-Фона окна инструментов вкладки, как выбран и не выбран|  
|WindowFrame|-Границы IDE|  
|WindowText|-Основной вкладке автоматического скрытия<br />-Передний план вкладку окна выбранное средство<br />-Вкладка окна документа без фокуса ввода и без фокуса ввода или невыделенного временной вкладке переднего плана<br />-Переднего плана по умолчанию представление и древовидного при наведении на глиф невыбранные<br />-Граница выделенной вкладки окна инструментов<br />— Фона бегунка полосы прокрутки границы и глифа|  
  
##  <a name="BKMK_ExposingColorsForEndUsers"></a> Предоставление цвета для конечных пользователей  
  
### <a name="overview"></a>Обзор  
 Иногда требуется разрешить конечным пользователям изменять пользовательский Интерфейс, например при создании кода редактора или конструктора. Наиболее распространенный способ сделать это — с помощью **Сервис > Параметры** диалоговое окно. — Если не имеют очень специализированную пользовательский Интерфейс, который требует специальных элементов управления, самый простой способ представления настройки **шрифты и цвета** странице в **среды** части диалогового окна. Для каждого элемента, которые предоставляют для настройки пользователь может изменить цвет переднего плана и цвет фона.  
  
### <a name="building-a-vspackage-for-your-customizable-colors"></a>Создание VSPackage для настраиваемые цвета  
 Пакет VSPackage можно управлять шрифты и цвета, через пользовательские категории и отображения элементов на странице свойств шрифты и цвета. Если вы используете этот механизм, пакеты VSPackage должны реализовывать [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) интерфейса и его связанных интерфейсах.  
  
 В принципе этот механизм можно использовать для изменения, все существующие элементы отображения и категории, которые содержат их. Тем не менее его не следует изменять категории текстовый редактор или своих отображаемых элементов. Дополнительные сведения о категории текстовый редактор, см. в разделе [шрифт и цвет Обзор](https://msdn.microsoft.com/library/bb165065.aspx).  
  
 Чтобы реализовать пользовательские категории и отображать элементы, пакет VSPackage должен удовлетворять следующим требованиям:  
  
-   **Создание или определение категорий в реестре.** Реализация IDE **шрифты и цвета** страницу свойств использует эти сведения для правильно запроса служба, поддерживающая данной категории.  
  
-   **Создайте или укажите группы в реестре (необязательно).** Возможно, рекомендуется определить группу, которая представляет объединение двух или более категорий. Если определен группу, интегрированной среды разработки автоматически выполняет слияние подкатегории и распространяет отображаемых элементов в пределах группы.  
  
-   **Реализация поддержки интегрированной среды разработки.**  
  
-   **Обрабатывать изменения шрифта и цвета.**  
  
#### <a name="to-create-or-identify-categories"></a>Для создания и определения категорий  
 Создать специальный тип категории записи реестра в разделе [HKLM\SOFTWARE\Microsoft \Visual Studio\\< версия Visual Studio\>\FontAndColors\\< категории\>]. \<Категория > нелокализованное имя категории.  
  
 Добавить в реестр с двумя значениями:  
  
|name|Тип|Данные|Описание:|  
|----------|----------|----------|-----------------|  
|Категория|REG_SZ|Идентификатор GUID|Идентификатор GUID, созданный для идентификации категории|  
|Пакет|REG_SZ|Идентификатор GUID|Идентификатор GUID VSPackage службы, которая поддерживает категории|  
  
 Служба, указанная в реестр необходимо предоставить реализацию [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) для соответствующей категории.  
  
#### <a name="to-create-or-identify-groups"></a>Чтобы создать или определить группы  
 Создать специальный тип категории записи реестра в разделе [HKLM\SOFTWARE\Microsoft \Visual Studio\\< версия Visual Studio\>\FontAndColors\\< группы\>]. \<группы > нелокализованное имя группы.  
  
 Добавить в реестр с двумя значениями:  
  
|name|Тип|Данные|Описание:|  
|----------|----------|----------|-----------------|  
|Категория|REG_SZ|Идентификатор GUID|Идентификатор GUID, созданный для идентификации категории|  
|Пакет|REG_SZ|Идентификатор GUID|Идентификатор GUID VSPackage службы, которая поддерживает категории|  
  
 Служба, указанная в реестр необходимо предоставить реализацию **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** для соответствующей группы.  
  
 ![IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a-fontandcolorgroup.png "0304 a_FontAndColorGroup")  
  
### <a name="to-implement-ide-support"></a>Для реализации поддержки интегрированной среды разработки  
 Реализуйте [GetObject](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), который возвращает либо [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) интерфейс или **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** интерфейс в интегрированную среду разработки для каждой категории или группы указан GUID.  
  
 Для каждой категории, он поддерживает, VSPackage реализует отдельный экземпляр [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) интерфейс.  
  
 Методы реализуется через [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) необходимо указать с помощью интегрированной среды разработки:  
  
- Список отображаемых элементов в категории  
  
- Локализуемые имена для отображаемых элементов  
  
- Отображаемые сведения для каждого элемента категории  
  
  **Примечание:** каждой категории должен содержать хотя бы один элемент для отображения.  
  
  Интегрированная среда разработки использует **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** интерфейса позволяет определить объединение несколько категорий.  
  
  Его реализация предоставляет интегрированную среду разработки с помощью:  
  
- Список категорий, входящие в состав указанной группы  
  
- Доступ к экземплярам [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) поддержки каждой категории в группе  
  
- Имена локализуемых групп  
  
#### <a name="updating-the-ide"></a>Обновление интегрированной среды разработки  
 Интегрированная среда разработки кэширует сведения о параметрах шрифта и цвета. Таким образом после внесения изменений конфигурации интегрированной среды разработки шрифта и цвета, обеспечивая актуальность кэша рекомендуется.  
  
 Обновление кэша осуществляется с помощью [IvsFontAndColorCacheManager](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) интерфейс и может быть выполнено глобально или только на выбранных элементов.  
  
### <a name="handling-font-and-color-changes"></a>Обработка изменения шрифта и цвета  
 Для правильной поддержки цветовое выделение текста, который отображает VSPackage, выделение цветом служба, поддерживающая VSPackage должен отвечать на инициированного пользователем изменения, внесенные на странице свойств «шрифты и цвета».  
  
 Чтобы сделать это, пакет VSPackage должен удовлетворять следующим требованиям:  
  
- **обрабатывать события, вызываемые IDE** путем реализации [IVsFontAndColorEvents](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) интерфейс. Интегрированная среда разработки вызывает соответствующий метод следующие пользовательские изменения страницы шрифты и цвета. Например, он вызывает [onfontchanged и задает](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) метод, если выбран новый шрифт.  
  
  **ИЛИ**  
  
- **опрос интегрированной среды разработки для изменения**. Это можно сделать через реализовать систему [IVsFontAndColorStorage](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) интерфейс. Несмотря на то что в основном для поддержки сохраняемости, [GetItem](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) метода можно получить данные шрифта и цвета для отображаемых элементов. Дополнительные сведения о параметры шрифта и цвета, см. в статье MSDN [параметры доступа к хранятся шрифта и цвета](https://msdn.microsoft.com/library/bb166382.aspx).  
  
  **Примечание:** убедитесь, что результаты опроса верны, использовать [IVsFontAndColorCacheManager](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) интерфейс, чтобы определить необходимость сброса кэша и обновления перед вызовом методов извлечения [ IVsFontAndColorStorage](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) интерфейс.  
  
#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Регистрация пользовательского шрифта и цвета категории без реализации интерфейсов  
 В следующем примере кода показано, как зарегистрировать пользовательский шрифт и цветовые категории без реализации интерфейсов:  
  
```xml  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]  
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"  
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"  
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"  
  
    "NameID"=dword:00000064  
```  
  
 **ПРИМЕЧАНИЕ.**  
  
-   «NameID» = идентификатор ресурса в пакете имя локализованной категории  
  
-   «ToolWindowPackage» = идентификатор GUID пакета  
  
-   «Категория» = «{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}» указан для примера и фактическое значение может быть новый идентификатор GUID, предоставленные средством реализации.  
  
### <a name="set-the-font-and-color-property-category-guid"></a>Задайте свойства категории шрифтов и цветов GUID  
 В примере кода показано задание GUID категории.  
  
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
