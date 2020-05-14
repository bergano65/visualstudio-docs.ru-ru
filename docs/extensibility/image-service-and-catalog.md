---
title: Обслуживание изображений и Каталог Документы Майкрософт
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79e1ccfad2a678656bcf09e37852532a8b28eb0e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710387"
---
# <a name="image-service-and-catalog"></a>Служба изображений и каталог
Эта поваренная книга содержит рекомендации и лучшие практики для принятия Visual Studio Image Service и Каталог изображений, представленный в Visual Studio 2015.

 Сервис изображений, представленный в Visual Studio 2015, позволяет разработчикам получать лучшие изображения для устройства и выбранную пользователем тему для отображения изображения, включая исправление тематики для контекста, в котором они отображаются. Принятие службы изображения поможет устранить основные болевые точки, связанные с обслуживанием активов, HDPI масштабирования, и тематики.

|||
|-|-|
|**Проблемы сегодня**|**Решения**|
|Смешение фонового цвета|Встроенное альфа-смешивание|
|Тематические (некоторые) изображения|Метаданные темы|
|Режим высокой контрастности|Альтернативные ресурсы высокой контрастной|
|Нужны несколько ресурсов для различных режимов DPI|Выбираемые ресурсы с векторным запасом|
|Дублирование изображений|Один идентификатор на концепцию изображения|

 Зачем внедрять сервис изображений?

- Всегда получайте последнее "идеальное" изображение от Visual Studio

- Вы можете отправлять и использовать свои собственные изображения

- Нет необходимости тестировать изображения при добавлении Windows нового масштабирования DPI

- Устранение старых архитектурных препятствий в реализации

  Панель инструментов оболочки Visual Studio до и после использования службы изображения:

  ![Служба изображений "до" и "после"](../extensibility/media/image-service-before-and-after.png "Служба изображений "до" и "после"")

## <a name="how-it-works"></a>Принцип работы
 Служба изображений может предоставить битотовое изображение, подходящее для любой поддерживаемой платформы uI:

- WPF: BitmapИсточник

- WinForms: System.Drawing.Bitmap

- Win32: HBITMAP

  Диаграмма потока обслуживания изображения

  ![Схема потока службы изображений](../extensibility/media/image-service-flow-diagram.png "Схема потока службы изображений")

  **Изображения прозвища**

  Кличка изображения (или кличка для краткости) — это пара GUID/ID, которая однозначно идентифицирует актив изображения или список изображений в библиотеке изображений.

  **Известные прозвища**

  Набор кликеров изображений, содержащихся в каталоге изображений Visual Studio и публично расходуемых любым компонентом или расширением Visual Studio.

  **Файлы манифеста изображения**

  Файлы изображения (*.imagemanifest*) — это файлы XML, которые определяют набор активов изображений, моникеры, представляющие эти активы, а также реальные изображения или изображения, представляющие каждый актив. Манифесты изображений могут определять автономные изображения или списки изображений для устаревшей поддержки uI. Кроме того, есть атрибуты, которые могут быть установлены либо на активе, либо на отдельных изображениях, лежащих в основе каждого актива, чтобы изменить, когда и как эти активы отображаются.

  **Схема манифеста изображения**

  Полный манифест изображения выглядит следующим образом:

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Import, Guid, ID, or String elements -->
      </Symbols>
      <!-- zero or one Images elements -->
      <Images>
        <!-- zero or more Image elements -->
      </Images>
      <!-- zero or one ImageLists elements -->
      <ImageLists>
        <!-- zero or more ImageList elements -->
      </ImageLists>
</ImageManifest>
```

 **Символы**

 В качестве помощи для читаемости и обслуживания манифест изображения может использовать символы для значений атрибутов. Символы определяются следующим образом:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|||
|-|-|
|**Вложенный элемент**|**Определение**|
|Импорт|Импортирует символы данного файла манифеста для использования в текущем манифесте|
|Guid|Символ представляет GUID и должен соответствовать форматированию GUID|
|ID|Символ представляет идентификатор и должен быть неотрицательным|
|Строка|Символ представляет произвольное значение строки|

 Символы чувствительны к случаям и ссылаются с помощью синтаксиса $(символ-имя):

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Некоторые символы предопределены для всех манифестов. Они могут быть использованы в \<атрибуте \<Uri> или элементе импорта> для ссылки на локальной машине.

|||
|-|-|
|**Символ**|**Описание**|
|CommonProgramFiles|Значение переменной среды %CommonProgramFiles%|
|ЛокальныеAppData|Значение переменной среды %LocalAppData%|
|МанифестФолдер|Папка, содержащая файл манифеста|
|MyDocuments|Полный путь папки "Мои документы" текущего пользователя|
|ProgramFiles|Значение переменной среды %ProgramFiles%|
|Система|Папка *Windows-System32*|
|Windir|Значение переменной среды %WinDir%|

 **ОС контейнера**

 Элемент \<> изображения определяет изображение, на которое можно ссылаться по прозвищу. GUID и ID, вместе взятые, образуют псевдоним изображения. Прозвище для изображения должно быть уникальным во всей библиотеке изображений. Если более одного изображения имеет заданное прозвище, то при создании библиотеки сохраняется первое изображение.

 Он должен содержать по крайней мере один источник. Нейтральные по размеру источники дадут наилучшие результаты в широком диапазоне размеров, но они не требуются. Если службе предлагается изображение размера, не \<определенного в элементе> изображения и нет нейтрального для размера источника, служба выберет наилучший источник для конкретного размера и масштабирует его до запрашиваемого размера.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**Атрибут**|**Определение**|
|Guid|(Обязательно) GUID часть моникера изображения|
|ID|(Обязательно) Идентификационная часть моникера изображения|
|РазрешитьColorInversion|(Необязательно, по умолчанию верно) Указывает, может ли изображение иметь свои цвета программно перевернуты при использовании на темном фоне.|

 **Источник**

 Элемент \<«Источник> определяет один ресурс источника изображения» (XAML и PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**Атрибут**|**Определение**|
|URI|(Обязательно) URI, который определяет, где изображение может быть загружено. Может принимать одно из следующих значений:<br /><br /> - [Пакет URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) с использованием application:/// органа<br />- Абсолютная ссылка на ресурс компоненты<br />- Путь к файлу, содержащему родной ресурс|
|Историческая справка|(Необязательно) Указывает, что на виде фона источник предназначен для использования.<br /><br /> Может принимать одно из следующих значений:<br /><br /> *Свет:* Источник может быть использован на светлом фоне.<br /><br /> *Темный:* Источник может быть использован на темном фоне.<br /><br /> *HighContrast:* Источник может использоваться на любом фоне в режиме высокой контрастности.<br /><br /> *HighContrastLight:* Источник может использоваться на светлом фоне в режиме высокой контрастности.<br /><br /> *HighContrastDark:* Источник может использоваться на темном фоне в режиме High Contrast.<br /><br /> Если атрибут фона опущен, источник может быть использован на любом фоне.<br /><br /> Если фон *Светлый,* *Темный,* *HighContrastLight*, или *HighContrastDark*, цвета источника никогда не инвертируются. Если фон опущен или установлен на *HighContrast,* инверсия цветов источника контролируется атрибутом **AllowColorInversion** изображения.|

Элемент \<> источник может иметь точно один из следующих дополнительных подэлементов:

||||
|-|-|-|
|**Элемент**|**Атрибуты (все требуется)**|**Определение**|
|\<Размер>|Значение|Источник будет использоваться для изображений данного размера (в блоках устройств). Изображение будет квадратным.|
|\<> SizeRange|MinSize, MaxSize|Источник будет использоваться для изображений от MinSize до MaxSize (в устройствах) включительно. Изображение будет квадратным.|
|\<Размеры>|Width, Height|Источник будет использоваться для изображений заданной ширины и высоты (в блоках устройств).|
|\<Размернаядальность>|Минвайн, МинВейт,<br /><br /> MaxWidth, MaxHeight|Источник будет использоваться для изображений от минимальной ширины/высоты до максимальной ширины/высоты (в единицах устройства) включительно.|

 Элемент \<«Источник>» также \<может иметь дополнительный подэлемент \<NativeResource>, который определяет> источника, загруженную из родной сборки, а не из управляемой сборки.

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**Атрибут**|**Определение**|
|Type|(Обязательно) Тип родного ресурса, xAML или PNG|
|ID|(Обязательно) Различная часть родного ресурса|

 **Imagelist**

 Элемент \<ImageList> определяет набор изображений, которые могут быть возвращены в одной полосе. Полоса построена по требованию, по мере необходимости.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**Атрибут**|**Определение**|
|Guid|(Обязательно) GUID часть моникера изображения|
|ID|(Обязательно) Идентификационная часть моникера изображения|
|External|(Необязательно, по умолчанию ложный) Указывает, ссылается ли кличка изображения на изображение в текущем манифесте.|

 Кличка для содержащегося изображения не должна ссылаться на изображение, определенное в текущем манифесте. Если содержащееся изображение не может быть найдено в библиотеке изображений, на его месте будет использовано пустое изображение заполнителя.

## <a name="using-the-image-service"></a>Использование службы изображений

### <a name="first-steps-managed"></a>Первые шаги (управляемые)
 Чтобы воспользоваться службой изображений, необходимо добавить ссылки на некоторые или все следующие сборки в проекте:

- *Microsoft.VisualStudio.ImageCatalog.dll*

  - Требуется, если вы используете встроенный каталог изображений **Известные Monikers**.

- *Microsoft.VisualStudio.Imaging.dll*

  - Требуется, если вы используете **CrispImage** и **ImageThemingUtilities** в вашем WPF UI.

- *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*

  - Требуется, если вы используете типы **ImageMoniker** и **ImageAttributes.**

  - **EmbedInteropTypes** должны быть настроены на истину.

- *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime*

  - Требуется, если вы используете тип **IVsImageService2.**

  - **EmbedInteropTypes** должны быть настроены на истину.

- *Microsoft.VisualStudio.Utilities.dll*

  - Требуется, если вы используете **BrushToColorConverter** для **ImageThemingUtilities.ImageBackgroundColor** в вашем UI WPF.

- *Microsoft.VisualStudio.Shell. \<VSVersion>.0*

  - Требуется, если вы используете тип **IVsUIObject.**

- *Microsoft.VisualStudio.Shell.Interop.10.0.dll*

  - Требуется, если вы используете помощников, связанных с UI WinForms.

  - **EmbedInteropTypes** должны быть настроены на истину

### <a name="first-steps-native"></a>Первые шаги (родные)
 Чтобы воспользоваться службой изображений, необходимо включить некоторые или все следующие заголовки в свой проект:

- **KnownImageIds.h**

  - Требуется, если вы используете встроенный каталог изображений **KnownMonikers**, но не может использовать тип **ImageMoniker,** например, при возвращении значений из **IVsHierarchy GetGuidProperty** или **GetProperty** звонки.

- **ИзвестныеMonikers.h**

  - Требуется, если вы используете встроенный каталог изображений **Известные Monikers**.

- **Параметры изображения140.h**

  - Требуется, если вы используете типы **ImageMoniker** и **ImageAttributes.**

- **VSShell140.h**

  - Требуется, если вы используете тип **IVsImageService2.**

- **ImageТемаУтилита.h**

  - Требуется, если вы не можете позволить службе изображения обрабатывать тематические для вас.

  - Не используйте этот заголовок, если служба изображения может обрабатывать ваши тематические изображения.

::: moniker range="vs-2017"
- **VSUIDPIHelper.h**

  - Требуется, если вы используете помощников DPI, чтобы получить текущий DPI.

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness.h**

  - Требуется, если вы используете помощников DPI осведомленности, чтобы получить текущий DPI.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>Как написать новый UI WPF?

1. Начните с добавления ссылок на сборку, необходимых в разделе вышеуказанных первых шагов, в проект. Вам не нужно добавлять все из них, так что добавьте только ссылки вам нужно. (Примечание: если вы используете или имеете доступ к **цветам** вместо **кистей,** то вы можете пропустить ссылку на **Утилиты**, так как вам не понадобится преобразователь.)

2. Выберите нужное изображение и получите его прозвище. Используйте **KnownMoniker**, или использовать свой собственный, если у вас есть свои собственные пользовательские изображения и прозвища.

3. Добавьте **CrispImages** в свой XAML. (См. ниже пример.)

4. Установите свойство **ImageThemingUtilities.ImageBackgroundColor** в иерархии uI. (Это должно быть установлено в месте, где цвет фона известен, не обязательно на **CrispImage**.) (См. ниже пример.)

```xaml
<Window
  x:Class="WpfApplication.MainWindow"
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">
  <Window.Resources>
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>
  </Window.Resources>
  <StackPanel Background="White" VerticalAlignment="Center"
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />
  </StackPanel>
</Window>
```

 **Как обновить существующий uI WPF?**

 Обновление существующего UI WPF является относительно простым процессом, который состоит из трех основных этапов:

1. Замените \<все элементы image \<> в вашем uI элементами CrispImage>.

2. Измените все атрибуты Исхода на атрибуты Moniker.

    - Если изображение никогда не меняется, и вы используете **KnownMonikers**, а затем статично связать это свойство **с KnownMoniker**. (См. приведенный выше пример.)

    - Если изображение никогда не меняется, и вы используете свой собственный пользовательский образ, а затем статично привязать к вашему собственному прозвищу.

    - Если изображение может измениться, свяжите атрибут Moniker с свойством кода, которое уведомляет об изменениях свойства.

3. Где-то в иерархии uI, установить **ImageThemingUtilities.ImageBackgroundColor,** чтобы убедиться, что цвет инверсия работает правильно.

    - Это может потребовать использования класса **BrushToColorConverter.** (См. приведенный выше пример.)

## <a name="how-do-i-update-win32-ui"></a>Как обновить uii Win32?
 Добавьте следующее в свой код там, где это уместно, чтобы заменить необработанную загрузку изображений. Коммутировать значения для возвращения HBITMAPs против HICONs против HIMAGELIST по мере необходимости.

 **Получите службу изображений**

```cpp
CComPtr<IVsImageService2> spImgSvc;
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);
```

 **Запрос изображения**

::: moniker range="vs-2017"

```cpp
ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

::: moniker range=">=vs-2019"

```cpp
UINT dpiX, dpiY;
HWND hwnd = // get the HWND where the image will be displayed
VsUI::CDpiAwareness::GetDpiForWindow(hwnd, &dpiX, &dpiY);

ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = dpiX;
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

## <a name="how-do-i-update-winforms-ui"></a>Как обновить uii WinForms?
 Добавьте следующее в свой код там, где это уместно, чтобы заменить необработанную загрузку изображений. Переключите значения для возврата Bitmaps по сравнению с иконками по мере необходимости.

 **Полезно с помощью оператора**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **Получите службу изображений**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **Запрос изображения**

::: moniker range="vs-2017"

```csharp
ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiHelper.DeviceDpiX;
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

::: moniker range=">=vs-2019"

```csharp
Control control = // get the control where the image will be displayed

ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiAwareness.GetWindowDpi(control.Handle);
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Как использовать кликеры изображений в новом окне инструмента?
 Шаблон проекта пакетного проекта VSIX был обновлен для Visual Studio 2015. Чтобы создать новое окно инструмента, нажмите правой кнопкой мыши на проект VSIX и выберите **Добавить** > **новый пункт** (**Ctrl**+**Shift**+**A**). Под уздом Extensibility для языка проекта выберите **окно пользовательского инструмента,** дайте окну инструмента имя и нажмите кнопку **Добавить.**

 Это ключевые места для использования кликеров в окне инструмента. Следуйте инструкциям для каждого из них:

1. Вкладка окна инструмента, когда вкладки становятся достаточно маленькими (также используется в коммутаторе окна **Ctrl**+**Tab).**

    Добавьте эту строку к конструктору для класса, который происходит от типа **ToolWindowPane:**

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. Команда открыть окно инструмента.

    В файле *.vsct* для пакета отодвините кнопку команды окна инструмента:

   ```xml
   <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <!-- Replace this KnownMoniker with your desired ImageMoniker -->
     <Icon guid="ImageCatalogGuid" id="Blank" />
     <!-- Add this -->
     <CommandFlag>IconIsMoniker</CommandFlag>
     <Strings>
       <ButtonText>MyToolWindow</ButtonText>
     </Strings>
   </Button>
   ```

   **Как использовать кликеры изображений в существующем окне инструмента?**

   Обновление существующего окна инструментов для использования кликеров изображений аналогично шагам по созданию нового окна инструмента.

   Это ключевые места для использования кликеров в окне инструмента. Следуйте инструкциям для каждого из них:

3. Вкладка окна инструмента, когда вкладки становятся достаточно маленькими (также используется в коммутаторе окна **Ctrl**+**Tab).**

   1. Удалите эти строки (если они существуют) в конструкторе для класса, который происходит от типа **ToolWindowPane:**

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. Смотрите шаг #1 "Как я могу использовать изображения прозвища в новом окне инструмента?" раздел выше.

4. Команда открыть окно инструмента.

   - Смотрите шаг #2 "Как использовать кликеры изображений в новом окне инструмента?" раздел выше.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Как использовать кликеры изображений в файле .vsct?
 Обновление файла *.vsct,* как указано в прокомментированных строках ниже:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <!--  Include the definitions for images included in the VS image catalog -->
  <Include href="KnownImageIds.vsct"/>
  <Commands package="guidMyPackage">
    <Buttons>
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.
             In this case, we're using the Guid for the VS image catalog.
             Change the id attribute to be the ID of the desired image moniker. -->
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />
        <CommandFlag>DynamicVisibility</CommandFlag>
        <CommandFlag>DefaultInvisible</CommandFlag>
        <CommandFlag>DefaultDisabled</CommandFlag>
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>IconAndText</CommandFlag>
        <!-- Add the IconIsMoniker CommandFlag -->
        <CommandFlag>IconIsMoniker</CommandFlag>
        <Strings>
          <ButtonText>Quick Fixes...</ButtonText>
          <CommandName>Show Quick Fixes</CommandName>
          <CanonicalName>ShowQuickFixes</CanonicalName>
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>
        </Strings>
      </Button>
    </Buttons>
  </Commands>
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->
  <Symbols>
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">
      <IDSymbol name="cmdidMyCommand" value="0x9437" />
    </GuidSymbol>
  </Symbols>
</CommandTable>
```

 **Что делать, если мой файл .vsct также должен быть прочитан более старыми версиями Visual Studio?**

 Старые версии Visual Studio не распознают флаг команды **IconIsMoniker.** Вы можете использовать изображения из службы изображений на версиях Visual Studio, которые поддерживают его, но продолжать использовать старые изображения на старых версиях Visual Studio. Для этого вы оставите файл *.vsct* без изменений (и, следовательно, совместимый со старыми версиями Visual Studio) и создадите файл CSV (связанные с \<комма- идентификатора), который отображает карты из пар GUID/ID, определенных в Bitmaps *.vsct*> элемент к парам image moniker GUID/ID.

 Формат картографии CSV файла:

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 Файл CSV развертывается с пакетом, а его местоположение определяется свойством **IconMappingFilename** атрибута пакета **ProvideMenuResource:**

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 **IconMappingFilename** — это либо относительный путь, неявно укорененный в $PackageFolder $ (как в приведенном выше примере), либо абсолютный путь, явно укорененный в каталоге, определяемом переменной среды, например, *«%UserProfile%»dir2»dir2»MyMappingFile.*

## <a name="how-do-i-port-a-project-system"></a>Как портировать проектную систему?
 **Как поставить ImageMonikers для проекта**

1. Реализовать **VSHPROPID_SupportsIconMonikers** на **IVsHierarchy**проекта , и вернуться верно.

2. Реализовать либо **VSHPROPID_IconMonikerImageList** (если исходный проект **использовался VSHPROPID_IconImgList)** или **VSHPROPID_IconMonikerGuid,** **VSHPROPID_IconMonikerId,** **VSHPROPID_OpenFolderIconMonikerGuid,** **VSHPROPID_OpenFolderIconMonikerId** (если в первоначальном проекте использовались **VSHPROPID_IconHandle** и **VSHPROPID_OpenFolderIconHandle).**

3. Измените реализацию исходных VSHPROPIDs для иконок для создания "устаревших" версий иконок, если точки расширения запрашиваются их. **IVsImageService2** предоставляет функциональность, необходимую для получения этих иконок

   **Дополнительные требования к ароматизаторам проекта VB/C**

   Только реализовать **VSHPROPID_SupportsIconMonikers,** если вы обнаружите, что ваш проект является **внешним вкусом.** В противном случае, фактический внешний вкус не может поддерживать изображения прозвища в реальности, и ваш базовый вкус может эффективно "скрыть" настроенные изображения.

   **Как использовать кликеры изображений в CPS?**

   Настройка пользовательских изображений в CPS (Общая проектная система) может быть выполнена вручную или через шаблон элемента, который поставляется с SDK Project System.

   **Использование проектной системы Расширяемые SDK**

   Следуйте инструкциям в [Provide custom icons для типа project Type/Item](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) для настройки изображений CPS. Более подробную информацию о CPS можно найти в [документации по расширяемости проектной системы Visual Studio](https://github.com/Microsoft/VSProjectSystem)

   **Ручное использование ImageMonikers**

4. Внедрить и экспортировать интерфейс **IProjectTreeModifier** в вашей проектной системе.

5. Определите, какой **известный Moniker** или пользовательский псевдоним изображения вы хотите использовать.

6. В методе **ApplyModifications** сделайте следующее где-нибудь в методе, прежде чем вернуть новое дерево, аналогичное приведенной ниже примеру:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. Если вы создаете новое дерево, вы можете установить пользовательские изображения, передавая в желаемых прозвищах в метод NewTree, похожий на приведенный ниже пример:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();
   ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();

   return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,
                                                /*filePath*/<value>,
                                                /*browseObjectProperties*/<value>,
                                                icon,
                                                expandedIcon);
   ```

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Как преобразовать из реальной полосы изображения в полосу изображений на основе моникера?
 **Мне нужно поддержать HIMAGELISTS**

 Если уже существует полоса изображений для кода, которую вы хотите обновить, чтобы использовать службу изображений, но вы ограничены AI, требующими прохождения списков изображений, вы все равно можете получить преимущества службы изображений. Чтобы создать полосу изображения на основе моникеров, выполните ниже те шаги, чтобы создать манифест из существующих кликеров.

1. Запустите инструмент **ManifestFromResources,** передав ему полоску изображения. Это создаст манифест для полосы.

   - Рекомендуем: укажите имя без значения по умолчанию для манифеста, чтобы удовлетворить его использование.

2. Если вы используете только **KnownMonikers**, а затем сделать следующее:

   - Замените \<> раздел изображения \<с изображениями/>.

   - Удалите все иные иксы подизображения (все, что с \<изображением>_) ).

   - Рекомендуется: переименовать символ AssetsGuid и символ полосы изображения в соответствии с его использованием.

   - Замените каждый **ContainedImage's**GUID с $(ImageCatalogGuid), замените\<каждый **containedImage's**ID с $(>), и добавьте внешний атрибут "истинного" к каждому **ContainedImage**

       - \<прозвище> должно быть заменено **на knownMoniker,** который соответствует изображению, но с "Известные Monikers". удалены из имени.

   - Добавим\\ <Импорт Ный манифест"."(ManifestFolder)\><Относительная установка dir путь к\* »Microsoft.VisualStudio.ImageCatalog.imagemanifest" /> в верхней части \<раздела символов>.

       - Относительный путь определяется местом развертывания, определенным в авторстве установки для манифеста.

3. Запустите инструмент **ManifestToCode** для генерации оберток, чтобы существующий код получил кличка, который он может использовать для запроса службы изображения для полосы изображения.

   - Рекомендуется: укажите имена без дефолта для оберток и именных пространств в соответствии с их использованием.

4. У все добавляет, настройки авторизации / развертывания, и другие изменения кода для работы с службой изображений и новых файлов.

   Пример манифеста, включаввв в себя как внутренние, так и внешние изображения, чтобы увидеть, как он должен выглядеть:

```xml
<?xml version="1.0"?>
<ImageManifest
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">

  <Symbols>
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest
         where $(ManifestFolder) is the deployed location of this manifest. -->
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />

    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />
    <ID Name="MyImage_0" Value="100" />
    <ID Name="MyImage_1" Value="101" />
    <ID Name="InternalList" Value="1001" />
    <ID Name="ExternalList" Value="1002" />
  </Symbols>

  <Images>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">
      <Source Uri="$(Resources)/MyImage_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">
      <Source Uri="$(Resources)/MyImage_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>

  <ImageLists>
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />
    </ImageList>
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />
    </ImageList>
  </ImageLists>

</ImageManifest>
```

 **Мне не нужно поддерживать HIMAGELISTS**

1. Определите набор **известных Monikers,** которые соответствуют изображениям в полосе изображения, или создайте свои собственные прозвища для изображений в полосе изображения.

2. Обновление любого отображения вы использовали, чтобы получить изображение на требуемом индексе в полосе изображения, чтобы использовать прозвища вместо.

3. Обновите код, чтобы использовать службу изображений, чтобы запросить прозвища с помощью обновленного отображения. (Это может означать обновление **CrispImages** для управляемого кода или запрос HBITMAPs или HICONs из службы изображений и передачу их для родного кода.)

## <a name="testing-your-images"></a>Тестирование изображений
 Вы можете использовать инструмент Image Library Viewer для проверки манифестов изображения, чтобы убедиться, что все написано правильно. Вы можете найти инструмент в [Visual Studio 2015 SDK](visual-studio-sdk.md). Документацию для этого инструмента и других можно найти [здесь](/visualstudio/extensibility/internals/vssdk-utilities?view=vs-2015).

## <a name="additional-resources"></a>Дополнительные ресурсы

### <a name="samples"></a>Примеры
 Некоторые из образцов Visual Studio на GitHub были обновлены, чтобы показать, как использовать службу изображения как часть различных точек расширяемости Visual Studio.

 Проверьте [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) наличие последних образцов.

### <a name="tooling"></a>Инструменты
 Набор инструментов поддержки для Службы изображений был создан для оказания помощи в создании/обновлении uI, который работает с Службой изображений. Для получения дополнительной информации о каждом инструменте, проверьте документацию, которая поставляется с инструментами. Инструменты включены в состав [Визуальной студии 2015 SDK](visual-studio-sdk.md).

 **МанифестИзРесурсы**

 Инструмент Manifest from Resources принимает список ресурсов изображений (PNG или XAML) и генерирует файл манифеста изображения для использования этих изображений с помощью службы изображений.

 **Манифесттокод**

 Инструмент Manifest to Code принимает файл манифеста изображения и генерирует файл обертки для ссылки на значения манифеста в коде (C q, C, или VB) или *.vsct* файлы.

 **ImageLibraryViewer**

 Инструмент Image Library Viewer может загружать манифесты изображения и позволяет пользователю манипулировать ими так же, как Visual Studio, чтобы убедиться, что манифест написан правильно. Пользователь может изменять фон, размеры, настройки DPI, High Contrast и другие настройки. Он также отображает информацию о загрузке, чтобы найти ошибки в манифестах и отображает исходную информацию для каждого изображения в манифесте.

## <a name="faq"></a>ВОПРОСЫ И ОТВЕТЫ

- Существуют ли какие-либо зависимости, которые необходимо включить при загрузке \<Ссылка Включить "Microsoft.VisualStudio." . Interop.14.0.DesignTime" />?

  - Установите EmbedInteropTypes"true" на всех интероп DLLs.

- Как развернуть манифест изображения с расширением?

  - Добавьте файл *.imagemanifest* в проект.

  - Установить "Включить в VSIX" к True.

- Я обновляю свою систему проектов CPS. Что случилось с **ImageName** и **StockIconService?**

  - Они были удалены, когда CPS был обновлен для использования моникеров. Вам больше не нужно звонить **в StockIconService**, просто передать желаемый **KnownMoniker** методу или свойству, используя метод расширения **ToProjectSystemType ()** в утилитах CPS. Вы можете найти отображение от **ImageName** к **известным Monikers** ниже:

    |||
    |-|-|
    |**ImageName**|**ИзвестныйМоникер**|
    |Image-имя.OfflineWebApp|KnownImageIds.web|
    |ImageName.WebСсылкиФодер|KnownImageIds.web|
    |ImageName.OpenReferenceFolder|ИзвестныеImageIds.FolderOpened|
    |ImageName.ReferenceFolder|KnownImageIds.Справка|
    |ImageName.Справка|KnownImageIds.Справка|
    |ImageName.SdlWebСправка|ИзвестныйImageIds.WebReferenceFolder|
    |ImageName.DiscoWebСправка|ИзвестныйImageIds.DynamicDiscoveryДокумент|
    |ImageName.Folder|ИзвестныеImageIds.FolderClosed|
    |ImageName.OpenFolder|ИзвестныеImageIds.FolderOpened|
    |ImageName.ExcludedFolder|ИзвестныеImageIds.HiddenFolderClosed|
    |ImageName.OpenExcludedFolder|ИзвестныеImageIds.HiddenFolderОткрыт|
    |ImageName.ExcludedFile|ИзвестныеImageIds.HiddenFile|
    |ImageName.DependentFile|ИзвестныйImageIds.GenerateFile|
    |ImageName.MissingFile|ИзвестныеImageIds.DocumentWarning|
    |ImageName.WindowsForm|ИзвестныеImageIds.WindowsForm|
    |ImageName.WindowsUserControl|ИзвестныеImageIds.UserControl|
    |ImageName.WindowsКомпонент|ИзвестныеИзображенияИ.КомпонентФайл|
    |ImageName.XmlSchema|ИзвестныеImageIds.XMLSchema|
    |ImageName.XmlFile|ИзвестныеImageIds.XMLFile|
    |ImageName.WebForm|KnownImageIds.web|
    |Image-сайт.WebService|ИзвестныйImageIds.WebService|
    |ImageName.WebUserControl|ИзвестныйImageIds.WebUserControl|
    |ImageName.WebCustomUserControl|ИзвестныйImageIds.WebCustomControl|
    |ImageName.AspPage|ИзвестныеImageIds.ASPFile|
    |ImageName.GlobalApplicationClass|ИзвестныеImageIds.SettingsFile|
    |ImageName.WebConfig|ИзвестныйImageIds.ConfigurationFile|
    |ImageName.HtmlPage|ИзвестныйImageIds.HTMLFile|
    |ImageName.StyleSheet|ИзвестныйImageIds.StyleSheet|
    |ImageName.ScriptFile|ИзвестныеImageIds.JSScript|
    |ImageName.TextFile|ИзвестныеИзображенияИ.Документ|
    |ImageName.SettingsFile|KnownImageIds.Настройки|
    |ImageName.Ресурсы|ИзвестныеImageIds.DocumentGroup|
    |ImageName.Bitmap|ИзвестныеИзображения.Изображение|
    |ImageName.Icon|ИзвестныеImageIds.iconFile|
    |ImageName.Image|ИзвестныеИзображения.Изображение|
    |ImageName.ImageMap|ИзвестныеImageIds.ImageMapFile|
    |ImageName.XWorld|ИзвестныйImageIds.XWorldFile|
    |ImageName.Audio|KnownImageIds.Sound|
    |ImageName.Видео|ИзвестныеИзображенияИ.Медиа|
    |ImageName.Cab|ИзвестныеImageIds.CABПроект|
    |ImageName.Jar|ИзвестныеImageIds.JARFile|
    |ImageName.DataEnvironment|ИзвестныеИзображенияИ.DataTable|
    |ImageName.PreviewFile|ИзвестныеImageIds.Report|
    |ImageName.DanglingСправка|ИзвестныеImageIds.ReferenceWarning|
    |ImageName.XsltFile|ИзвестныеImageIds.XSLTransform|
    |ImageName.Cursor|ИзвестныеImageIds.CursorFile|
    |ImageName.AppDesignerFolder|KnownImageIds.Property|
    |ImageName.Data|KnownImageIds.Database|
    |ImageName.Application|ИзвестныеИзображенияИ.Приложение|
    |ImageName.DataSet|ИзвестныеImageIds.DatabaseGroup|
    |ImageName.Pfx|ИзвестныеИзображенияИ.Сертификат|
    |ImageИмя.Snk|ИзвестныеИзображенияИ.Правило|
    |ImageName.VisualBasicProject|ИзвестныеImageIds.VBProjectNode|
    |ImageName.CSharpProject|ИзвестныеImageIds.CSProjectNode|
    |ImageName.Empty|KnownImageIds.Blank|
    |ImageName.MissingFolder|ИзвестныеImageIds.FolderOffline|
    |ImageName.SharedImportСправка|ИзвестныеImageIds.SharedProject|
    |ImageName.SharedProjectCs|ИзвестныеImageIds.CSSharedProject|
    |ImageName.SharedProjectVc|ИзвестныеImageIds.CPPSharedProject|
    |ImageName.SharedProjectJs|ИзвестныйImageIds.JSSharedProject|
    |ImageName.CSharpCodeFile|ИзвестныеImageIds.CSFileNode|
    |ImageName.VisualBasicCodeFile|ИзвестныйImageIds.VBFileNode|

  - Я обновляю мой поставщик списка завершений. Что **известные Моники** соответствуют старым значениям **StandardGlyphGroup** и **StandardGlyph?**

    ||||
    |-|-|-|
    |GlyphGroupClass|GlyphItemPublic|КлассОбщественность|
    |GlyphGroupClass|GlyphItemInternal|КлассВнутренний|
    |GlyphGroupClass|GlyphItemFriend|КлассВнутренний|
    |GlyphGroupClass|GlyphItemProtected|КлассЗащищенный|
    |GlyphGroupClass|GlyphItemPrivate|КлассЧастный|
    |GlyphGroupClass|GlyphItemShortcut|КлассШорт|
    |GlyphGroupConstant|GlyphItemPublic|КонстантПублично|
    |GlyphGroupConstant|GlyphItemInternal|КонстантВнутренний|
    |GlyphGroupConstant|GlyphItemFriend|КонстантВнутренний|
    |GlyphGroupConstant|GlyphItemProtected|КонстантЗащищенные|
    |GlyphGroupConstant|GlyphItemPrivate|ConstantPrivate|
    |GlyphGroupConstant|GlyphItemShortcut|ConstantShortcut|
    |Делегат GlyphGroup|GlyphItemPublic|ДелегатПублично|
    |Делегат GlyphGroup|GlyphItemInternal|ДелегатВнутренние|
    |Делегат GlyphGroup|GlyphItemFriend|ДелегатВнутренние|
    |Делегат GlyphGroup|GlyphItemProtected|ДелегатЗащищенный|
    |Делегат GlyphGroup|GlyphItemPrivate|ДелегатЧастный|
    |Делегат GlyphGroup|GlyphItemShortcut|ДелегатКороткий|
    |ГлифGroupЕнум|GlyphItemPublic|EnumerationPublic|
    |ГлифGroupЕнум|GlyphItemInternal|ПеречислениеВнутренний|
    |ГлифGroupЕнум|GlyphItemFriend|ПеречислениеВнутренний|
    |ГлифGroupЕнум|GlyphItemProtected|ПеречислениеЗащищено|
    |ГлифGroupЕнум|GlyphItemPrivate|EnumerationPrivate|
    |ГлифGroupЕнум|GlyphItemShortcut|EnumerationShortcut|
    |GlyphGroupEnumMember|GlyphItemPublic|EnumerationItemPublic|
    |GlyphGroupEnumMember|GlyphItemInternal|EnumerationПунктInternal|
    |GlyphGroupEnumMember|GlyphItemFriend|EnumerationПунктInternal|
    |GlyphGroupEnumMember|GlyphItemProtected|EnumerationItemProtected|
    |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationItemPrivate|
    |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationItemShortcut|
    |GlyphGroupEvent|GlyphItemPublic|EventPublic|
    |GlyphGroupEvent|GlyphItemInternal|EventInternal|
    |GlyphGroupEvent|GlyphItemFriend|EventInternal|
    |GlyphGroupEvent|GlyphItemProtected|Защита событий|
    |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|
    |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|
    |GlyphGroupИсключение|GlyphItemPublic|ИсключениеОбщественное|
    |GlyphGroupИсключение|GlyphItemInternal|ИсключениеВнутренние|
    |GlyphGroupИсключение|GlyphItemFriend|ИсключениеВнутренние|
    |GlyphGroupИсключение|GlyphItemProtected|ИсключениеЗащищено|
    |GlyphGroupИсключение|GlyphItemPrivate|ИсключениеЧастные|
    |GlyphGroupИсключение|GlyphItemShortcut|ИсключениеШорт|
    |GlyphGroupField|GlyphItemPublic|ФилдПубличн|
    |GlyphGroupField|GlyphItemInternal|ФилдВнутренний|
    |GlyphGroupField|GlyphItemFriend|ФилдВнутренний|
    |GlyphGroupField|GlyphItemProtected|ПолеЗащищеное|
    |GlyphGroupField|GlyphItemPrivate|ФилдПритенен|
    |GlyphGroupField|GlyphItemShortcut|ФилдШорт|
    |GlyphGroupInterface|GlyphItemPublic|ИнтерфейсПубличная|
    |GlyphGroupInterface|GlyphItemInternal|ИнтерфейсВнутренний|
    |GlyphGroupInterface|GlyphItemFriend|ИнтерфейсВнутренний|
    |GlyphGroupInterface|GlyphItemProtected|ИнтерфейсЗащищенный|
    |GlyphGroupInterface|GlyphItemPrivate|ИнтерфейсЧастный|
    |GlyphGroupInterface|GlyphItemShortcut|ИнтерфейсШорт|
    |GlyphGroupMacro|GlyphItemPublic|МакроОбщественность|
    |GlyphGroupMacro|GlyphItemInternal|Макровнутренний|
    |GlyphGroupMacro|GlyphItemFriend|Макровнутренний|
    |GlyphGroupMacro|GlyphItemProtected|Макрозащищенные|
    |GlyphGroupMacro|GlyphItemPrivate|Макрочастный|
    |GlyphGroupMacro|GlyphItemShortcut|МакроШортск|
    |GlyphGroupMap|GlyphItemPublic|КартаПубличная|
    |GlyphGroupMap|GlyphItemInternal|КартаВнутренние|
    |GlyphGroupMap|GlyphItemFriend|КартаВнутренние|
    |GlyphGroupMap|GlyphItemProtected|КартаЗащищенная|
    |GlyphGroupMap|GlyphItemPrivate|MapPrivate|
    |GlyphGroupMap|GlyphItemShortcut|MapShortcut|
    |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|
    |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|
    |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|
    |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|
    |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|
    |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|
    |GlyphGroupMethod|GlyphItemPublic|МетодПубличная|
    |GlyphGroupMethod|GlyphItemInternal|МетодВнутренний|
    |GlyphGroupMethod|GlyphItemFriend|МетодВнутренний|
    |GlyphGroupMethod|GlyphItemProtected|MethodProtected|
    |GlyphGroupMethod|GlyphItemPrivate|МетодЧастный|
    |GlyphGroupMethod|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupOverload|GlyphItemPublic|МетодПубличная|
    |GlyphGroupOverload|GlyphItemInternal|МетодВнутренний|
    |GlyphGroupOverload|GlyphItemFriend|МетодВнутренний|
    |GlyphGroupOverload|GlyphItemProtected|MethodProtected|
    |GlyphGroupOverload|GlyphItemPrivate|МетодЧастный|
    |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupModule|GlyphItemPublic|МодульПубличная|
    |GlyphGroupModule|GlyphItemInternal|МодульВнутренний|
    |GlyphGroupModule|GlyphItemFriend|МодульВнутренний|
    |GlyphGroupModule|GlyphItemProtected|МодульЗащищенный|
    |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|
    |GlyphGroupModule|GlyphItemShortcut|ModuleShortcut|
    |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|
    |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|
    |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|
    |GlyphGroupNamespace|GlyphItemProtected|Названиезащищенное пространство|
    |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|
    |GlyphGroupOperator|GlyphItemPublic|ОператорПубличная|
    |GlyphGroupOperator|GlyphItemInternal|ОператорВнутренний|
    |GlyphGroupOperator|GlyphItemFriend|ОператорВнутренний|
    |GlyphGroupOperator|GlyphItemProtected|ОператорЗащищено|
    |GlyphGroupOperator|GlyphItemPrivate|ОператорЧастный|
    |GlyphGroupOperator|GlyphItemShortcut|ОператорКороткий|
    |GlyphGroupProperty|GlyphItemPublic|НедвижимостьПубличная|
    |GlyphGroupProperty|GlyphItemInternal|НедвижимостьВнутренний|
    |GlyphGroupProperty|GlyphItemFriend|НедвижимостьВнутренний|
    |GlyphGroupProperty|GlyphItemProtected|НедвижимостьЗащищенная|
    |GlyphGroupProperty|GlyphItemPrivate|НедвижимостьЧастный|
    |GlyphGroupProperty|GlyphItemShortcut|НедвижимостьКороткий|
    |GlyphGroupStruct|GlyphItemPublic|СтруктураПубличная|
    |GlyphGroupStruct|GlyphItemInternal|СтруктураВнутренние|
    |GlyphGroupStruct|GlyphItemFriend|СтруктураВнутренние|
    |GlyphGroupStruct|GlyphItemProtected|СтруктураЗащищенная|
    |GlyphGroupStruct|GlyphItemPrivate|СтруктураЧастный|
    |GlyphGroupStruct|GlyphItemShortcut|СтруктураШорт|
    |GlyphGroupTemplate|GlyphItemPublic|ШаблонПубличная|
    |GlyphGroupTemplate|GlyphItemInternal|ШаблонВнутренний|
    |GlyphGroupTemplate|GlyphItemFriend|ШаблонВнутренний|
    |GlyphGroupTemplate|GlyphItemProtected|ШаблонЗащищенный|
    |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|
    |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|
    |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|
    |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|
    |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|
    |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|
    |GlyphGroupType|GlyphItemPublic|TypePublic|
    |GlyphGroupType|GlyphItemInternal|TypeInternal|
    |GlyphGroupType|GlyphItemFriend|TypeInternal|
    |GlyphGroupType|GlyphItemProtected|ТипЗащищенный|
    |GlyphGroupType|GlyphItemPrivate|TypePrivate|
    |GlyphGroupType|GlyphItemShortcut|TypeShortcut|
    |GlyphGroupUnion|GlyphItemPublic|UnionPublic|
    |GlyphGroupUnion|GlyphItemInternal|UnionInternal|
    |GlyphGroupUnion|GlyphItemFriend|UnionInternal|
    |GlyphGroupUnion|GlyphItemProtected|СоюзЗащищенный|
    |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|
    |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|
    |GlyphGroupПеременный|GlyphItemPublic|ФилдПубличн|
    |GlyphGroupПеременный|GlyphItemInternal|ФилдВнутренний|
    |GlyphGroupПеременный|GlyphItemFriend|ФилдВнутренний|
    |GlyphGroupПеременный|GlyphItemProtected|ПолеЗащищеное|
    |GlyphGroupПеременный|GlyphItemPrivate|ФилдПритенен|
    |GlyphGroupПеременный|GlyphItemShortcut|ФилдШорт|
    |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|
    |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemProtected|ValueTypeЗащищено|
    |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|
    |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|
    |GlyphGroupИнтринсик|GlyphItemPublic|ОбъектПубличная|
    |GlyphGroupИнтринсик|GlyphItemInternal|ObjectInternal|
    |GlyphGroupИнтринсик|GlyphItemFriend|ObjectInternal|
    |GlyphGroupИнтринсик|GlyphItemProtected|ОбъектЗащищенный|
    |GlyphGroupИнтринсик|GlyphItemPrivate|ObjectPrivate|
    |GlyphGroupИнтринсик|GlyphItemShortcut|ObjectShortcut|
    |GlyphGroupJSharpMethod|GlyphItemPublic|МетодПубличная|
    |GlyphGroupJSharpMethod|GlyphItemInternal|МетодВнутренний|
    |GlyphGroupJSharpMethod|GlyphItemFriend|МетодВнутренний|
    |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|
    |GlyphGroupJSharpMethod|GlyphItemPrivate|МетодЧастный|
    |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupJSharpField|GlyphItemPublic|ФилдПубличн|
    |GlyphGroupJSharpField|GlyphItemInternal|ФилдВнутренний|
    |GlyphGroupJSharpField|GlyphItemFriend|ФилдВнутренний|
    |GlyphGroupJSharpField|GlyphItemProtected|ПолеЗащищеное|
    |GlyphGroupJSharpField|GlyphItemPrivate|ФилдПритенен|
    |GlyphGroupJSharpField|GlyphItemShortcut|ФилдШорт|
    |GlyphGroupJSharpClass|GlyphItemPublic|КлассОбщественность|
    |GlyphGroupJSharpClass|GlyphItemInternal|КлассВнутренний|
    |GlyphGroupJSharpClass|GlyphItemFriend|КлассВнутренний|
    |GlyphGroupJSharpClass|GlyphItemProtected|КлассЗащищенный|
    |GlyphGroupJSharpClass|GlyphItemPrivate|КлассЧастный|
    |GlyphGroupJSharpClass|GlyphItemShortcut|КлассШорт|
    |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|
    |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItemProtected|Названиезащищенное пространство|
    |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|
    |GlyphGroupJSharpInterface|GlyphItemPublic|ИнтерфейсПубличная|
    |GlyphGroupJSharpInterface|GlyphItemInternal|ИнтерфейсВнутренний|
    |GlyphGroupJSharpInterface|GlyphItemFriend|ИнтерфейсВнутренний|
    |GlyphGroupJSharpInterface|GlyphItemProtected|ИнтерфейсЗащищенный|
    |GlyphGroupJSharpInterface|GlyphItemPrivate|ИнтерфейсЧастный|
    |GlyphGroupJSharpInterface|GlyphItemShortcut|ИнтерфейсШорт|
    |GlyphGroupОшибка||StatusError|
    |GlyphBscFile||ClassFile|
    |ГлифСобрание||Справочник|
    |ГлифБиблиотека||Библиотека|
    |ГлифВБПроект||ВБПроектНод|
    |GlyphCoolProject||CSProjectNode|
    |GlyphCppProject||CPPProjectNode|
    |GlyphDialogId||Диалог|
    |ГлифОПЕНФолдер||ФолдерОткрытой|
    |GlyphClosedFolder||ФолдерЗакрыт|
    |ГлифРоу||GoToNext|
    |GlyphCSharpFile||CSFileNode|
    |GlyphCSharpExpansion||Фрагмент кода|
    |ГлифКейворд||IntellisenseKeyword|
    |ГлифИнформация||СтатусИнформация|
    |ГлифСправка||ClassMethodReference|
    |ГлифРекурсия||Рекурсия|
    |GlyphXmlItem||Тег|
    |GlyphJSharpProject||DocumentCollection|
    |GlyphJSharpДокумент||Документ|
    |GlyphForwardType||GoToNext|
    |GlyphCallersГраф||CallTo|
    |GlyphCallGraph||CallFrom|
    |Предупреждение о глифе||StatusWarning|
    |GlyphMaybeСправка||ВопросМарк|
    |GlyphMaybeCaller||CallTo|
    |GlyphMaybeCall||CallFrom|
    |ГлифЭксипмметод||РасширениеМетод|
    |GlyphExtensionMethodInternal||РасширениеМетод|
    |GlyphExtensionMethodFriend||РасширениеМетод|
    |GlyphExtensionMethodProtected||РасширениеМетод|
    |GlyphExtensionMethodPrivate||РасширениеМетод|
    |GlyphExtensionMethodShortcut||РасширениеМетод|
    |GlyphXmlAttribute||XmlAttribute|
    |GlyphXmlChild||XmlElement|
    |GlyphXmlDescendant||XmlDescendant|
    |GlyphXmlNamespace||XmlNamespace|
    |GlyphXmlАтрибутВопрос||XmlAttributeLowConfidence|
    |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|
    |GlyphXmlChild||XmlElementLowConfidence|
    |GlyphXmlChildCheck||XmlElementHighConfidence|
    |GlyphXmlОтскинтерфаксВопрос||XmlDescendantLowConfidence|
    |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|
    |GlyphCompletionWarning||IntellisenseПредупреждение|
