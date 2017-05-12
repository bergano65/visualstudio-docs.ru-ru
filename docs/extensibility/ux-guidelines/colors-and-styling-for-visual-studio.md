---
title: "Цвета и стили для Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 4
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9524ecc3cadef58821fba857de8e82e59eea9b43
ms.openlocfilehash: 93bfad7dc919364770a7d225c09db8b432cf1be0
ms.contentlocale: ru-ru
ms.lasthandoff: 05/04/2017

---
# <a name="colors-and-styling-for-visual-studio"></a>Цвета и стили для Visual Studio
## <a name="using-color-in-visual-studio"></a>С помощью цвета в Visual Studio  
В Visual Studio цвет используется как средство связи не так же, как и оформления. Как минимум используйте цвет и зарезервировать его в ситуациях, где требуется:  
  
-   Связь значения или объединением (например, модификаторы платформы или языка)  
  
-   Привлечь внимание (например, указывающей на изменение состояния)  
  
-   Улучшить читаемость и укажите ориентиры для навигации в пользовательском Интерфейсе  
  
-   Увеличьте desirability  
  
Существует несколько вариантов для назначения цвета для элементов пользовательского интерфейса в Visual Studio. Иногда бывает трудно рисунок, какой параметр вы должны использовать или правильно использовать. В этом разделе помогут вам:  
  
1.  Понимать различных служб и систем, используемых для определения цветов в Visual Studio.  
  
2.  Выберите правильный параметр для данного элемента.  
  
3.  Правильно используйте параметр, которую вы выбрали.  
  
> **Примечание:** никогда не следует жестко кодировать hex, RGB или системные цвета для элементов пользовательского интерфейса. Использование служб обеспечивает гибкость в настройке цветовой тон. Кроме того, без этой службы будет невозможно воспользоваться преимуществами возможности переключения темы [службы VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).
  
### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Элементы интерфейса методы для назначения цвета для Visual Studio  
Выберите метод, наилучшим образом подходят элементы пользовательского интерфейса.  
  
| Пользовательский Интерфейс | Метод | Что это такое? |  
| --- | --- | --- |  
| С внедренными или автономный диалоговым окнам. | **Системные цвета** | Системными именами, позволяющие операционной системы определить цвет и внешний вид элементов пользовательского интерфейса, такие как общие элементы управления диалогового окна. |
| У вас есть пользовательский Интерфейс настраиваемой, должны быть согласованы с общей среды VS и имеется элементов пользовательского интерфейса, которые соответствуют категории и семантическое значение общего токенов. | **Стандартные общие цвета** | Существующие имена токенов стандартных цветов для определенных элементов пользовательского интерфейса |
| Необходим для отдельных компонентов или группы функций и общих цвет для аналогичных элементов отсутствует. | **Пользовательские цвета** | Цвет имена токенов, которые относятся к области и не предназначен для совместного использования с другой пользовательский Интерфейс |
| Вы хотите разрешить конечным пользователям изменять пользовательский Интерфейс или содержимого (например, текстовые редакторы или специализированные конструктора windows). | **Настройка конечного пользователя**<br /><br />**(Средства &gt; диалогового окна параметров)** | Параметры, заданные на странице «Шрифты и цвета» **средства &gt; параметры** диалогового окна или специализированные страницы, относящиеся к одной из возможностей пользовательского интерфейса. |
| У вас есть пользовательский Интерфейс, который создается в формате HTML. | **Daytona** | Позволяет пользовательскому Интерфейсу, созданные в формате HTML для доступа к службе цветов и шрифтов. |
  
### <a name="visual-studio-themes"></a>Тем Visual Studio  
Visual Studio функции три разных цветовых тем: светлую, темную или синюю. Он также определяет режим высокой контрастности, который используется во всей системе цветовой темы, предназначены для специальных возможностей.  
  
Пользователям будет предложено выбрать тему при их первом использовании Visual Studio и способны переключаться темы позже, перейдя **средства &gt; параметры &gt; среды &gt; Общие** и выбрать новую тему из меню «Цветовая тема».  
  
Пользователи также могут использовать панель управления для переключения их всей системы в один из нескольких тем высокой контрастности. Если пользователь выбирает тему с высокой контрастностью, затем Выбор цвета темы Visual Studio больше не влияет на цветов в Visual Studio, несмотря на то, что любое изменение темы сохраняются для, когда пользователь выходит из режима высокой контрастности. Дополнительные сведения о режиме высокой контрастности см. в разделе [Выбор вступили в силу](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).
  
### <a name="the-vscolor-service"></a>Служба VSColor  
Visual Studio предоставляет доступ к службе цвет среде, известных как VSColor службы, которое позволяет привязать значения цвета элементов пользовательского интерфейса для именованного запись, содержащая значения цвета для каждой темы Visual Studio. Это гарантирует, что цвета автоматически изменится в соответствии с текущей выбранной пользователем темы или системных режима высокой контрастности. Использование службы означает, что реализация все изменения цвета связанные темы обрабатывается в одном месте и при использовании стандартные общие цвета из службы пользовательского интерфейса автоматически отражают новые темы в будущих версиях Visual Studio.  
  
### <a name="implementation"></a>Реализация  
Исходный код Visual Studio включает несколько файлов определения пакета, содержащих списки имен токенов и соответствующих цветовых значений для каждой темы. Служба цвет считывает VSColors, определенные в этих файлах определений пакетов. Эти цвета ссылаются на языке XAML или в коде, а затем загружаются через `IVsUIShell5.GetThemedColor` метода или DynamicResource сопоставление.  
  
### <a name="system-colors"></a>Системные цвета  
Стандартные элементы управления ссылаться на системные цвета по умолчанию. Если требуется использовать системные цвета, как и при создании внедренного или на отдельном диалоговом пользовательского интерфейса не нужно выполнять никаких действий.  
  
### <a name="common-shared-colors-in-the-vscolor-service"></a>Стандартные общие цвета в службе VSColor  
Свои элементы интерфейса должны отражать общей среды Visual Studio. Используя стандартные общие цвета, которые подходят для компонентов пользовательского интерфейса, которые вы разрабатываете, убедитесь, что интерфейс согласуется с другими интерфейсами Visual Studio и что цветов будут обновляться автоматически при добавлении или обновлении темы.  
  
Прежде чем использовать стандартные общие цвета, убедитесь, что понимаете, как правильно использовать. Неправильное использование стандартные общие цвета может привести к несогласованной, утомительным или сбивающим с толку функционирования для пользователей.  
  
### <a name="user-customizable-colors"></a>Настраиваемые пользователем цвета  
См.: [предоставление цвета для конечных пользователей](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)  
  
В некоторых случаях требуется разрешить конечным пользователям настраивать пользовательский Интерфейс, как и при создании редактора кода или конструктора. Настраиваемые компоненты пользовательского интерфейса можно найти на **шрифты и цвета** раздел **средства &gt; параметры** диалоговое окно, где пользователям можно изменить цвет и цвет фона.  
  
![Средства &gt; диалогового окна параметров](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Средства &gt; диалогового окна параметров
  
### <a name="web-ui-colors"></a>Веб-цвета пользовательского интерфейса  
Он становится общим для создания компонентов пользовательского интерфейса с помощью HTML, чтобы их можно использовать как в Visual Studio Online, так и в среде Visual Studio. Пользовательский Интерфейс, написанного на HTML необходимо использовать службу VSColor при выполнении в среде Visual Studio. Сведения о Daytona и способ его использования см. в разделе [Daytona и веб-Интерфейсе](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_DaytonaAndWebUI).  
  
##  <a name="BKMK_TheVSColorService"></a>Служба VSColor  
Visual Studio предоставляет службе цвета среды, также называемое VSColor службы или службы цвет оболочки. Эта служба позволяет привязать значения цвета элементов пользовательского интерфейса в набор, содержащий цветов для каждой темы имя значение цвета. VSColor службы должен использоваться для всех элементов пользовательского интерфейса, чтобы цвета автоматически изменяются в соответствии с текущей темой, выбранные пользователем, а также, чтобы пользовательский Интерфейс привязан к службе цвета среды будут интегрироваться с новой темы в будущих версиях Visual Studio.  
  
### <a name="how-the-service-works"></a>Как работает служба  
Службы цвета среды считывает VSColors, определенный в .pkgdef для компонентов пользовательского интерфейса. Эти VSColors затем имеются ссылки в разметке XAML или кода, загружаются через `IVsUIShell5.GetThemedColor` или `DynamicResource` сопоставления.  
  
![Архитектура службы цвета среды](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Архитектура службы цвета среды разработки
  
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
  
##  <a name="BKMK_ChoosingHighContrastColors"></a>Выбор цвета высокой контрастности  
  
### <a name="overview"></a>Обзор  
Windows использует несколько тем системного уровня высокой контрастности, увеличьте контрастность цвет текста, цвет фона и изображений, делая элементов более отчетливым на экране. Для поддержки специальных возможностей очень важно, что элементы интерфейса Visual Studio правильно ответить, когда пользователи переходят высококонтрастную тему.  
  
Для режима высокой контрастности темы можно лишь небольшое количество системных цветов. При выборе системы имена цветов, помните следующие рекомендации:  
  
1.  **Выберите системных цветов, которые имеют одинаковое значение семантики** с элементом, выделение цветом. Например при выборе высокой контрастности цвет для текста в окне используйте WindowText и не ControlText.  
  
2.  **Выбрать пары переднего плана и фона** вместе или не быть уверены, выбранный цвет будет работать на всех тем высокой контрастности.  
  
3.  **Определить, какие части пользовательского интерфейса самые важные и убедитесь, что области содержимого будет выделяться.** Поэтому использование цвета границы строгого является стандартным для определения области содержимого, поскольку существуют варианты не цветов для различных областей содержимого множество подробных сведений, который обычно будет отличить небольшие отличия в цветового тона, будут потеряны.  
  
### <a name="system-color-set"></a>Набор системных цветов  
Таблицы на [блог команды разработчиков WPF: ссылка SystemColors](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) указывает полный набор имена системных цветов и соответствующий тона, отображаемых в каждой темы.  
  
При применении это ограниченный набор цветов к пользовательскому Интерфейсу *ожидается, будут потеряны слабая сведения, которые присутствовали в «normal» темы*. Ниже приведен пример пользовательского интерфейса с слабая серым цветом, которые используются для различения областей в окно инструментов. При совместном использовании то же окно, которое отображается в режиме высокой контрастности, вы увидите, что фон тот же оттенок и границы этих областей обозначаются границы сама по себе:  
  
![Примером как небольшие сведения могут быть потеряны при высокой контрастности](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Примером как небольшие сведения могут быть потеряны при высокой контрастности
  
#### <a name="choosing-text-colors-in-an-editor"></a>Выбор цвета текста в редакторе  
Чтобы указать значения, такие как разрешение для упрощения идентификации групп схожих элементов цветом текста используется в редакторе или в области конструктора. В тему с высокой контрастностью Однако у вас может различать более трех цветов текста. WindowText, GrayText и HotTrackText являются только цветов, доступных на поверхности WindowBackground. Поскольку нет возможности использовать более трех цветов, тщательно выберите наиболее важные отличия, которые нужно отобразить в режиме высокой контрастности.  
  
Оттенки каждого имена токенов, допустимое в рабочей области редактора, как они отображаются в каждом высококонтрастную тему:  
  
![Сравнение редактора высокой контрастности](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Сравнение редактора высокой контрастности
  
Примеры поверхности редактор в "голубой" теме.  
  
![Редактор в "голубой" теме](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Редактор в "Голубой" теме
  
![Редактор в теме высокой контрастности #1](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Редактор в теме высокой контрастности #1
  
### <a name="usage-patterns"></a>Использование шаблонов
Многие стандартные элементы пользовательского интерфейса, уже определено Высокая контрастность цветов. Эти шаблоны использования можно ссылаться при выборе собственной системы имена цветов, таким образом, согласованные с аналогичными компонентами элементы пользовательского интерфейса.  
  
| Системный цвет | Использование |
| --- | --- |
| ActiveCaption | -Active IDE и rafted окна глифы кнопка при наведении указателя мыши и нажмите клавишу<br />— Название фона панели для интегрированной среды разработки и rafted windows<br />-По умолчанию фон строки состояния |
| ActiveCaptionText | -Active IDE и rafted windows для заголовка панели передний план (текст и глифы)<br />-Фона и границы активного окна кнопки при наведении указателя мыши и нажмите клавишу |
| Control | -Поле со списком, раскрывающегося списка и поиск элемента управления по умолчанию и отключить фон, включая кнопку раскрывающегося списка<br />-Цвет фона кнопки целевой закрепления<br />-Фона панели команда<br />-Фон окна средство |
| ControlDark | -Фон IDE<br />-Разделители панель меню и команды<br />-Граница панели команда<br />-Shadows меню<br />-Средство разделитель и границы окна вкладка по умолчанию и при наведении курсора мыши<br />-Документов также цвет фона для кнопки переполнения<br />-Границы глифа целевой закрепления |
| ControlDarkDark |-Окно вкладки без фокуса ввода, выбранный документ |
| ControlLight |-Граница вкладки автоматического скрытия<br />-Границы списка поля со списком поле и раскрывающийся список<br />-Закрепить целевой фона и границ |
| ControlLightLight | -Установлен, имеющего фокус временной границы |
| ControlText | -Глиф список поля со списком поле и раскрывающийся список<br />-Текст вкладки окна, не выбранные средство |
| GrayText |-Поле со списком и раскрывающегося списка отключены границы, глиф раскрывающийся список, текст и текст пункта меню<br />— Текст отключенное меню<br />-Текст заголовка поиска элемент управления «параметры поиска»<br />-Разделитель секций поиска элемент управления |
| Выделение | -Все при наведении указателя мыши и нажатой цвет фона и границы, за исключением того, поле со списком поле разворачивающуюся кнопку документ и фона хорошо переполнения граница кнопки<br />-Фон выбранного элемента |
| HighlightText | -Все при наведении указателя мыши и нажатую foregrounds (текст и глифы)<br />-Конкретное средство документом и окном вкладки окна управления переднего плана<br />-Граница заголовка окна инструмента конкретное окно<br />-Фокус, выбранный временной вкладке переднего плана<br />-Граница кнопки переполнения хорошо документа при наведении указателя мыши и нажмите клавишу<br />-Границы выбранный значок|
| HotTrack | -Полоса прокрутки thumb фона и границ на машине<br />-Полосы прокрутки глиф нажмите клавишу со стрелкой |
| InactiveCaption | -Неактивные IDE и rafted окна глифы кнопка при наведении курсора мыши<br />— Название фона панели для интегрированной среды разработки и rafted windows<br />— Фон элемента управления отключенное поиска |
| InactiveCaptionText | -Неактивные IDE и rafted windows заголовка панели передний план (текст и глифы)<br />-Неактивного окна кнопки фона и границ при наведении курсора мыши<br />-Цвет фона кнопки окна инструментов без фокуса ввода и границы<br />-Передний план управления поиска отключено |
| Меню | -Фон раскрывающегося меню<br />-Фон флажка установлен и отключен |
| MenuText | -Границы раскрывающегося меню<br />-Метки<br />-Глифы меню<br />-Текст раскрывающегося меню<br />-Границы выбранный значок |  
| Полоса прокрутки | -Прокрутите панель и прокрутка стрелки фон, все состояния |
| Окно | -Вкладка фона автоматического скрытия<br />-Меню полосы, а команда фона Полка<br />-Фон вкладки окна документа без фокуса ввода или невыбранные и границу документа, для открытых и временной вкладок<br />-Фона панели заголовка окна инструмента без фокуса ввода<br />-Фон окна инструментов вкладки, как выбран и не выбрано |
| WindowFrame | -Границы IDE |
| WindowText | -Передний план вкладку автоматического скрытия<br />-Передний план вкладку окна выбранное средство<br />-Вкладка окна документа без фокуса ввода и без фокуса ввода или невыбранные временной вкладке переднего плана<br />-Дереве представления цвет переднего плана и при наведении указателя мыши на глиф невыбранные<br />-Граница выбранная вкладка окна инструментов<br />-Полосы прокрутки thumb фона, границы и глифа |
  
##  <a name="BKMK_ExposingColorsForEndUsers"></a>Предоставление доступа к цвета для конечных пользователей  
  
### <a name="overview"></a>Обзор  
Иногда может потребоваться разрешить конечным пользователям настраивать пользовательский Интерфейс, как и при создании редактора кода или конструктора. Наиболее распространенный способ сделать это — с помощью **средства &gt; параметры** диалогового окна. Если не имеют очень специализированную пользовательский Интерфейс, который требует специальных элементов управления, самый простой способ настройки представления является через **шрифты и цвета** страницы в пределах **среды** диалогового окна. Для каждого элемента, который предоставить для настройки пользователя можно изменить цвет и цвет фона.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Создание VSPackage для настраиваемых цветов  
Пакет VSPackage можно управлять шрифтов и цветов через пользовательские категории и отображения элементов на странице свойств шрифты и цвета. При использовании этого механизма, пакеты VSPackage должны реализовывать [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) интерфейса и его связанных интерфейсов.  
  
В принципе этот механизм может использоваться для изменения всех существующих отображаемые элементы и категории, которые их содержат. Тем не менее он должен использоваться не для изменения текстовый редактор или своих отображаемых элементов. Дополнительные сведения о категории текстового редактора в разделе [шрифт и цвет Обзор](https://msdn.microsoft.com/en-us/library/bb165065.aspx).  
  
Чтобы реализовать пользовательские категории или отображать элементы, пакет VSPackage должен удовлетворять следующим требованиям:  
  
-   **Создайте или определите категории в реестре.** Реализация IDE **шрифты и цвета** страница свойств использует эти сведения для запроса правильно для службы, поддерживающей данной категории.  
  
-   **Создайте или определите группы в реестре (необязательно).** Может быть полезно для определения группы, представляющий объединение двух или более категорий. При определении группы, интегрированной среды разработки автоматически выполняет слияние подкатегории и распространяет отображаемые элементы в пределах группы.  
  
-   **Реализация поддержки IDE.**  
  
-   **Обрабатывать изменения цвета и шрифта.**  
  
#### <a name="to-create-or-identify-categories"></a>Для создания и определения категорий  
Создать специальный тип категории запись реестра `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` где `<Category>` нелокализованное имя категории.
  
Добавить в реестр с двумя значениями:  

| Имя | Тип | Данные | Описание |
| --- | --- | --- | --- |
| Категория | REG_SZ | Идентификатор GUID | Идентификатор GUID, созданный для определения категории |
| Пакет | REG_SZ | Идентификатор GUID | Идентификатор GUID для пакета VSPackage службы, которая поддерживает категории |
  
 Службы, указанный в разделе реестра необходимо обеспечить реализацию [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) для соответствующей категории.  
  
#### <a name="to-create-or-identify-groups"></a>Для создания и определения групп  
Создать специальный тип категории запись реестра `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` где `<group>` нелокализованное имя группы.  
  
Добавить в реестр с двумя значениями:

| Имя | Тип | Данные | Описание |
|--- | --- | --- | --- |
| Категория | REG_SZ | Идентификатор GUID | Идентификатор GUID, созданный для определения категории |
| Пакет | REG_SZ | Идентификатор GUID | Идентификатор GUID для пакета VSPackage службы, которая поддерживает категории |
  
Службы, указанный в разделе реестра необходимо обеспечить реализацию `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` для соответствующей группы.

![Реализация интерфейса IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Реализация`IVsFontAndColorGroup`
  
### <a name="to-implement-ide-support"></a>Чтобы обеспечить поддержку интегрированной среды разработки  
Реализуйте [GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), которое возвращает либо [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) интерфейса или `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` интерфейс IDE для каждой категории или группы кодом GUID.  
  
Для каждой категории, он поддерживает, VSPackage реализует отдельный экземпляр [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) интерфейса.  
  
Методы реализуется с помощью [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) необходимо предоставить среду IDE:  
  
-   Списки элементов в категории  
  
-   Локализуемые имен для отображения элементов  
  
-   Отображаемые сведения для каждого элемента категории  
  
 > **Примечание:** каждой категории должен содержать хотя бы один элемент для отображения.
  
Интегрированная среда разработки использует `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` интерфейс, чтобы определить объединение несколько категорий.

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
  
 **ИЛИ**  
  
-   **опрос интегрированную среду разработки для изменения**. Это можно сделать с помощью реализовать систему [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) интерфейса. Несмотря на то что в основном для поддержки сохраняемости, [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) метода можно получить сведения о шрифт и цвет для отображения элементов. Дополнительные сведения о параметрах шрифтов и цветов см. в статье MSDN [параметров доступа к хранимых шрифта и](https://msdn.microsoft.com/en-us/library/bb166382.aspx).  
  
> **Примечание:** чтобы гарантировать правильность результатов опроса, используйте [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) интерфейс, чтобы определить необходимость сброса кэша и обновления перед вызовом методов получения [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) интерфейса.
  
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
-   `"NameID"` = Идентификатор ресурса имя локализованной категории в пакет
-   `"ToolWindowPackage"` = Идентификатор GUID пакета
-   `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"`всего лишь пример и фактическое значение может быть новый идентификатор GUID, предоставленный средством реализации.  
  
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
  
##  <a name="BKMK_DaytonaAndWebUI"></a>Daytona и веб-Интерфейс  
  
### <a name="overview"></a>Обзор  
«Daytona» — это набор API-интерфейсов, средств и служб, которые позволяют пользователю создавать подключаемые модули с HTML, CSS и JavaScript, который может использоваться в различных узлах, например Visual Studio или клавишу F12. Подключаемые модули состоят из переносимой компонент, который записывается в формате HTML, CSS и JavaScript, и дополнительные компоненты конкретного узла. Каждый узел Daytona может иметь свой собственный набор правил пользовательского интерфейса, явные и неявные, что подключаемый модуль должен соответствовать для отображения в машинном коде, в своей среде. Некоторые узлы, например в Visual Studio, конечные пользователи могут изменить тему по умолчанию «», чтобы визуальных аспектов узла не может быть ориентировано статически, при создании таблицы стилей. Это вызывает значительные затруднения для разработчиков, создающих переносимой подключаемых модулей. В этом разделе объясняется, как создать веб-интерфейса в Visual Studio с помощью Daytona узла, в результате которого правильно поддерживает темы и высокой контрастности.  
  
### <a name="daytona-theming-mechanism"></a>Механизм использования тем Daytona  
Среда выполнения Daytona предоставляет ряд служб, который абстрагирует соглашения пользовательского интерфейса и возможности использования тем узла. Эти службы убедиться, что подключаемые модули автоматически соответствуют visual ожиданий пользователя, в зависимости от среды, в которой они размещаются в. Это поведение предоставляются три основные компоненты:  
  
1.  Таблицы стилей, введенный среды выполнения (plugin.css), которая прозрачно применяет набор правил CSS для пользовательского интерфейса подключаемого модуля и стили HTML-элементов управления (например, HTMLInputElement и HTMLButtonElement набор по умолчанию  
  
2.  Набор хостом маркеров, которые можно использовать для стиля элементы пользовательского интерфейса, с помощью значений, которые основаны на тему вместо жестко задано  
  
    -  Декларативный синтаксис для доступа к эти токены с помощью CSS  
  
    -  API-Интерфейс для программного доступа к темы токены из JavaScript  
  
3.  Уведомления об изменениях темы  
  
#### <a name="runtime-injected-style-sheet"></a>Таблица стилей введенного среды выполнения  
Координаты Daytona среды выполнения с основным приложением для вставки стиля, автоматически страницу темы стандартные элементы пользовательского интерфейса подключаемого модуля. Это включает стили для следующие понятия:  
  
-   Шрифт среды разработки  
  
-   Цвета фона  
  
-   Гиперссылки  
  
-   Элементы управления формы (например: `<select>`, `<input>`,`<button>`  
  
-   Таблицы  
  
-   Заголовки  
  
-   Полосы прокрутки  
  
Это означает, что если пользовательский Интерфейс состоит только из стандартных элементов управления пользовательского интерфейса HTML, затем дополнительные действия должны быть требуются правильно реагировать на изменения темы и для поддержки высокой контрастности.  
  
#### <a name="custom-ui"></a>Настройка пользовательского интерфейса  
В случае почти во всех нетривиальных стандартные элементы управления пользовательского интерфейса HTML будет недостаточно для обеспечения завершения работы для подключаемого модуля, а должны вводиться настраиваемого пользовательского интерфейса. Для поддержки выбора и цвет используйте соответствующий шрифт, **токены темы** следует использовать либо декларативно в CSS, или непосредственно через API JavaScript, описанных ниже. Среда выполнения Daytona позаботится об обновлении таблиц стилей, использующие эти токены при загрузке подключаемого модуля и для изменения темы.  
  
##### <a name="theme-tokens"></a>Токены темы  
Доступны оба маркера темы стандартных и конкретного узла. Стандартные маркеры являются введенный узел и всегда доступен. Предпочтительнее использовать там, где возможно, используя стандартные токены. Стандартные маркеры гарантируется должны быть предоставлены всем узлам Daytona, а их использование позволяет подключаемого модуля по своей природе более переносимый код. Набор стандартных токенов может быть изменен на то, что должны быть добавлены только новые маркеры и не должна быть удалена. Версия Visual Studio 2013 описано ниже:  
  
| Имя токена | Описание |
| --- | --- |
| `plugin-background-color` | Цвет фона по умолчанию для использования подключаемого модуля |
| `plugin-color` | Цвет по умолчанию для использования подключаемого модуля |
| `plugin-contextmenu-active-color` | Цвет выделения по умолчанию для контекстного меню, когда они активны (иметь фокус) |
| `plugin-contextmenu-background-color` | Цвет фона по умолчанию для контекстного меню |
| `plugin-contextmenu-border-color` | Цвет границы по умолчанию для контекстного меню |
| `plugin-contextmenu-color` | Цвет по умолчанию для контекстного меню |
| `plugin-contextmenu-hover-color` | По умолчанию цвет фона при наведении указателя мыши для контекстного меню |
| `plugin-contextmenu-hover-text-color` | Цвет по умолчанию при наведении указателя мыши для контекстного меню |
| `plugin-contextmenu-icon-checkbox` | По умолчанию цвет значка флажок контекстные меню |
| `plugin-contextmenu-inactive-text-color` | По умолчанию цвет выделения для контекстных меню, когда они неактивны |
| `plugin-contextmenu-separator-color` | Цвет разделителя по умолчанию для контекстного меню |
| `plugin-font-family` | Семейство шрифтов по умолчанию для использования подключаемого модуля |
  
В Visual Studio, следующие `plugin-font` токены основаны на параметрах шрифт среды:  
  
-   `plugin-font-size`  
  
-   `plugin-font-weight`  
  
-   `plugin-highlight-background-color`  
  
-   `plugin-highlight-color`  
  
-   `plugin-inactive-color` 
  
Следующие `plugin-link` маркеры используются для стиля `HTMLElements` (гиперссылок):
  
-   `plugin-link-color`  
  
-   `plugin-link-active-color`  
  
-   `plugin-link-hover-color`  
  
Plugin.CSS стили полосы прокрутки по умолчанию, с помощью следующих маркеров для улучшения поддержки тем в различных узлах (в частности, Visual Studio):
  
-   `plugin-scrollbar-arrow-color`  
  
-   `plugin-scrollbar-background-color`  
  
-   `plugin-scrollbar-face-color`  
  
Следующие `plugin-select` маркеры используются для стиля `HTMLSelectElement` (поле со списком поле с раскрывающимся списком):  
  
-   `plugin-select-option-background-color` 
  
-   `plugin-select-option-color`  
  
-   `plugin-select-option-checked-background-color`  
  
-   `plugin-select-option-checked-border-color`  
  
-   `plugin-select-option-checked-foreground-color`  
  
-   `plugin-select-option-hover-background-color`  
  
-   `plugin-select-option-hover-border-color`  
  
-   `plugin-select-option-hover-foreground-color`  
  
-   `plugin-select-border-color`  
  
-   `plugin-select-background-color`  
  
-   `plugin-select-foreground-color`  
  
-   `plugin-select-hover-background-color`  
  
-   `plugin-select-hover-border-color`  
  
-   `plugin-select-hover-foreground-color`  
  
-   `plugin-table-border-color`  
  
-   `plugin-table-header-background-color`  
  
-   `plugin-table-header-color`  
  
-   `plugin-textbox-border-color`  
  
-   `plugin-textbox-background-color`  
  
-   `plugin-textbox-color`  
  
-   `plugin-textbox-disabled-background-color`  
  
-   `plugin-textbox-disabled-border-color`  
  
-   `plugin-textbox-disabled-color`  
  
Эти токены, которые должны использоваться для *все* дерева представлений и таблиц, так как они имеют правильные значения по умолчанию, установите в различных узлах для поддержки тем и высокая контрастность:  
  
-   `plugin-treeview-content-background-color`  
  
-   `plugin-treeview-content-color` 
  
-   `plugin-treeview-content-inactive-selected-color`  
  
-   `plugin-treeview-content-mouseover-background-color`  
  
-   `plugin-treeview-content-mouseover-color`  
  
-   `plugin-treeview-content-inactive-selected-color`  
  
-   `plugin-treeview-content-selected-background-color`  
  
-   `plugin-treeview-content-selected-border-color`  
  
-   `plugin-treeview-content-selected-color`  
  
##### <a name="host-specific-tokens"></a>Токены конкретного узла  
Помимо поддержки стандартный набор токенов, узлы также может предоставлять нестандартное маркеры. Host в Visual Studio достигается путем предоставления подключаемый модуль для задания маркера псевдонимов темы в разделе Visual Studio конкретного манифеста. Пример:
  
```  
"vs": {  
    "theme_token_aliases": {   
        "diagnostics-host-border": {   
            "category": "f8a8b2a5-dd35-43f6-a382-fd6a61325c22",   
            "key_type": "BackgroundColor",   
            "name": "Border"   
        },   
        ...   
    }   
}    
```  
  
 В этом примере представлены токен темы, с именем `diagnostics-host-border`, который может ссылаться одинаково на стандартные токены, упомянутых выше. `category`, `key_type`, И `name` разрешаются цвет `IVsFontAndColorStorage` интерфейса. Во многих случаях можно найти соответствующие цвета (вместе с `category`, `key_type`, и `name` сведения) в XML-файлах, расположенных в `VSCommonContent\themes`. Такой же механизм используется в том случае, если пакет появились новые настраиваемые цвета: соответствует `category`, `key_type`, и `name` в цвет, который вы хотите использовать. Авторы подключаемый модуль должен пытаться использовать стандартные токены, когда это возможно и использовать только маркеры конкретного узла в случае крайней необходимости.  
  
##### <a name="using-theme-tokens-in-css"></a>Использование токенов темы в CSS  
 Токены темы называются синтаксис специально форматированного комментария. Правила для синтаксического анализа токена.  
  
1.  Комментарий выражения должны быть заключены в квадратные скобки (`[ ]`).  
  
2.  Все пробелы в пределах комментария, но за пределами выражения, учитывается.  
  
3.  Выражение комментарий должен следовать непосредственно свойство, которое оно заменяет.  
  
4.  Будут удалены все начальные и конечные пробелы в выражении.  
  
5.  Имя каждого маркера в пределах выражения должны заключаться в фигурные скобки (например, `{font-family}` и `{button-hover-color}`). В противном случае он будет рассматриваться как буквенное значение.  
  
 Ниже приведены примеры как токенов средства синтаксического анализа, заменят значения CSS, при условии, что `plugin-background-color` маркер имеет значение `#000` и `plugin-font-family` маркер имеет значение `Verdana`.
  
| Созданные CSS | Проанализированное CSS | Примечания |  
| --- | --- | --- |
| `background-color: #fff; /*[{plugin-background-color}]*/` | `background-color: #000;` | Значение по умолчанию заменяется динамическое значение конкретного узла. |  
| `background-color: #fff; /*   [{plugin-background-color}]   */` | `background-color: #000;` | Пробелы, находящиеся за пределами выражения игнорируются. |  
| `background-color: #fff; /*[   {plugin-background-color}   ]*/` | `background-color: #000;` | Завершающие и начальные пробелы в выражении усекаются. |
| `background-color: #fff; /*{plugin-background-color}*/` | `background-color: #fff;` | Выражение не заключается в квадратные скобки, и таким образом комментария учитывается. |
| `background-color: #fff; /*[plugin-background-color]*/` | `background-color: plugin-background-color;` | Маркер не заключен в фигурные скобки и поэтому обрабатывается как буквенное значение. |
| `/*[{plugin-background-color}]*/ background-color: #fff;` | `background-color: #fff;` | Комментарий не соответствует соглашениям значение свойства и поэтому учитывается. |
| `background-color: #fff;  /*[{plugin-background-color}]*/` | `background-color: #fff;`| *Таким же, как описано выше.* |
| `/*[{plugin-background-color}]*/  background-color: #fff;` | `background-color: #fff;` | *Таким же, как описано выше.* |
| `font-family: Arial, sans-serif; /*[{plugin-font-family}, sans-serif]*/` | `font-family: Verdana, sans-serif;` | Замена маркера и сохранен только текстовое содержимое. |
| `background-image: linear-gradient(0% #000, 100% #ccc); /*[linear-gradient(0% #000, 100% {plugin-background-color})]*/` | `background-image: linear-gradient(0% #000, 100% #000);` | *Таким же, как описано выше.* |
  
Если CSS-файл включает темы токены он должен быть помечен `data-plugin-theme` для атрибута `link` элемента в HTML-файле. Пример:  
  
```  
<link href="default.css" rel="stylesheet" data-plugin-theme="true" />  
```

##### <a name="using-theme-tokens-from-javascript"></a>Использование токенов тему из JavaScript  
Пользовательский Интерфейс должен быть темой, CSS, где это возможно, существуют сценарии, когда значение темы маркера необходимо получить программным образом. Например, если пользовательский Интерфейс настраиваемой рисуется на `CanvasElement` , не наследуют стили CSS, или если элемент пользовательского интерфейса которые динамически создаются в отличие от ссылки на таблицы стилей. Сценарии включены с помощью Daytona API `Plugin.Theme.getValue`. Эта функция возвращает значение для заданного имени токена хостом темы.  
  
| Не включен в тему | Темы |
| --- | --- |
| `var surface = document.getElementById("surface").getContext("2d");  surface.fillStyle = "#ccc";  surface.fillRect(0, 0, 200, 200);` | `var surface = document.getElementById("surface").getContext("2d");  surface.fillStyle = ("plugin-background-color");  surface.fillRect(0, 0, 200, 200);` |
| `var el = document.createElement("div");  el.style.backgroundColor = "#ccc";` | `var el = document.createElement("div");  el.style.backgroundColor = Plugin.Theme.getValue("plugin-background-color");` |  
  
Если маркеры используются в коде JavaScript, **события изменения темы, которые должны обрабатываться чтобы откликаться на обновления**. Это необязательно для темы маркерами декларативно в CSS, как среда выполнения Daytona берет на себя его для использования подключаемого модуля. Тема события могут обрабатываться следующим образом:

**Член (один обработчик)**
```
Plugin.Theme.onchange = function () 
{
    // re-draw dynamic UI here
}
```

**DOM-события (несколько обработчиков)**
```
Plugin.Theme.addEventListener("change", function () 
{
    // re-draw dynamic UI here
});
```
  
В этом случае было бы очень часто, чтобы повторно вызвать `Plugin.Theme.getValue` в эти обработчики в качестве значения токенов темы, скорее всего, изменяться при изменении темы.  
  
##### <a name="standard-token-mapping"></a>Стандартная сопоставления маркеров  
Стандартные токены, сопоставляются с цвета среды и оболочки. Ниже представлены вида, эти сопоставления.  
  
| Имя токена | Сопоставление VS (`EnvironmentColors`) |  
| --- | --- |  
| `plugin-color` | `ToolWindowTextColorKey` |
| `plugin-background-color` | `ToolWindowBackgroundColorKey` |
| `plugin-link-color` | `ControlLinkTextColorKey` |
| `plugin-link-hover-color` | `ControlLinkTextHoverColorKey` |
| `plugin-link-active-color` | `ControlLinkTextPressedColorKey` |
| `plugin-highlight-color` | `HighlightTextColorKey` |
| `plugin-highlight-background-color` | `HighlightColorKey` |
| `plugin-table-header-background-color` | `GridHeadingBackgroundColorKey` |
| `plugin-table-header-color` | `GridHeadingTextColorKey` |
| `plugin-table-border-color` | `GridLineColorKey` |
| `plugin-button-background-color` | `ButtonFaceColorKey` |
| `plugin-button-hover-background-color` | `ButtonHighlightColorKey` | 
| `plugin-button-color` | `ButtonTextColorKey` |
| `plugin-button-border-color` | `ButtonBorderColorKey` |
  
##### <a name="theme-changes"></a>Изменения темы  
Visual Studio узла триггеры подключаемого модуля изменения темы при конечный пользователь вносит изменения в следующие параметры:  
  
**Цвет темы:**  
  
![Изменения цветовой темы](../../extensibility/ux-guidelines/media/0305-a_colortheme.png "0305-a_ColorTheme")<br />Изменения цветовой темы  
  
**Темы среды:**  
  
![Изменения темы среды](../../extensibility/ux-guidelines/media/0305-b_environmenttheme.png "0305-b_EnvironmentTheme")<br />Изменения темы среды  
  
**Темы операционной системы** (только при изменении в и из режима высокой контрастности):  
  
![Изменения темы операционной системы](../../extensibility/ux-guidelines/media/0305-c_ostheme.png "0305-c_OSTheme")<br />Изменения темы операционной системы
