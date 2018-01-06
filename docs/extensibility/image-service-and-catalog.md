---
title: "Изображения службы и каталога | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
caps.latest.revision: "37"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6f5d31e28c47dbcd4f17f7f1e1bc0ac6a8755d5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="image-service-and-catalog"></a>Служба изображений и каталога
Это руководство содержит рекомендации и советы и рекомендации по внедрению изображений службы Visual Studio и каталог образа, представленные в Visual Studio 2015.  
  
 Служба образов, представленные в Visual Studio 2015 позволяет разработчикам получать лучший изображения для устройства и выбранной темы пользователя для отображения изображения, включая правильный темы для контекста, в котором они отображаются. Внедрение служба образов позволит избежать основных Проблемные вопросы, связанные с средства обслуживания, HDPI масштабирование и темы.  
  
|||  
|-|-|  
|**Сегодня проблем**|**Решения**|  
|Смешение цвета фона|Встроенные альфа-смешение|  
|Изображения темы (некоторые)|Метаданные темы|  
|Режим высокой контрастности|Альтернативный ресурсы Высокая контрастность|  
|Требуется несколько ресурсов для разных режимов точек на ДЮЙМ|Можно выбрать ресурсами с помощью векторной fallback|  
|Повторяющиеся изображения|Один идентификатор каждого изображения концепции|  
  
 Почему внедрить изображение службы?  
  
-   Последний образ «пикселей точно», всегда получите из Visual Studio  
  
-   Вы можете отправить и использовать свои собственные образы  
  
-   Не нужно проверять, когда операционная система Windows добавляет новый масштабирование изображений  
  
-   Адрес старого архитектуры препятствий в реализации  
  
 Панели инструментов Visual Studio shell до и после применения образа службы:  
  
 ![Служба изображений до и после](../extensibility/media/image-service-before-and-after.png "служба изображений до и после")  
  
## <a name="how-it-works"></a>Принцип работы  
 Служба образов можно ввести растровый рисунок, подходящий для любой поддерживаемой платформы пользовательского интерфейса:  
  
-   WPF: BitmapSource  
  
-   WinForms: System.Drawing.Bitmap  
  
-   Win32: HBITMAP  
  
 Схема потока службы изображений  
  
 ![Схема потока службы изображений](../extensibility/media/image-service-flow-diagram.png "схема потока службы изображений")  
  
 **Моникеры изображения**  
  
 Моникер изображения (или моникера для краткости) представляет собой пару GUID или идентификатор, уникально идентифицирует ресурс изображения или списка ресурса изображения в библиотеке изображений.  
  
 **Известные моникеров**  
  
 Набор моникеров изображения, содержащихся в Visual Studio изображение каталога и публично может быть использован в любой компонент Visual Studio или расширение.  
  
 **Файлы манифеста изображения**  
  
 Файлы манифеста (.imagemanifest) изображение, XML-файлы, которые определяют набор ресурсов изображений, моникеров, которые представляют эти ресурсы и реальных изображения или изображения, представляющие каждый актив. Манифестов изображений можно определить автономные изображения или списки изображений для поддержки устаревшего кода пользовательского интерфейса. Кроме того существуют атрибуты, которые могут быть установлены на ресурс или на отдельных изображений за каждый актив Чтобы изменить условия и способ отображения этих ресурсов.  
  
 **Схема манифеста изображения**  
  
 Завершение создания образа манифест выглядит следующим образом:  
  
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
  
 Как помочь читаемость и обслуживание, манифест изображения можно использовать символы для значений атрибутов. Символы, которые определены следующим образом:  
  
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
|**Дочерний элемент**|**Определение**|  
|Импорт|Импортирует символов для заданного файла манифеста для использования в текущий манифест|  
|Guid|Символ представляет собой идентификатор GUID и должно соответствовать форматирование GUID|  
|ID|Символ представляет идентификатор и должно быть неотрицательным целым числом|  
|String|Произвольное строковое значение представляет символ|  
  
 Символы, с учетом регистра и с использованием синтаксиса $(symbol-name) упоминаемого:  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 Некоторые символы являются стандартными для всех манифестов. Они используются в атрибуте Uri \<источника > или \<импорта > элемент пути для ссылок на локальном компьютере.  
  
|||  
|-|-|  
|**Символ**|**Описание**|  
|CommonProgramFiles|Значение переменной среды % CommonProgramFiles %|  
|LocalAppData|Значение переменной среды % LocalAppData %|  
|ManifestFolder|Папка, содержащая файл манифеста|  
|Мои документы|Полный путь папки «Мои документы» текущего пользователя|  
|ProgramFiles|Значение переменной среды % ProgramFiles %|  
|Система|В папку Windows\System32|  
|WinDir|Значение переменной среды % WinDir %|  
  
 **Изображение**  
  
 \<Изображение > элемент определяет изображение, которое может ссылаться моникера. GUID и ID в совокупности образуют моникер изображения. Моникер изображения должно быть уникальным для всего изображения библиотеки. Если более одного изображения данного моникера, первое вхождение во время построения библиотеки является тот, который сохраняется.  
  
 Он должен содержать хотя бы один источник. Зависит от размера источников позволит получить лучшие результаты для широкого размеров, но они не требуются. Если служба получает запрос на изображения размером не определенные в \<изображение > элемент и не указан источник зависит от размера, служба выберите лучшим источником определенного размера и масштабировать его до требуемого размера.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**Attribute (XElement Dynamic Property)** (Attribute (динамическое свойство XElement))|**Определение**|  
|Guid|[Обязательно] GUID для моникер изображения|  
|ID|[Обязательно] Идентификатор часть моникер изображения|  
|AllowColorInversion|[Необязательно, значение по умолчанию true] Указывает, возможно ли изображение его цвета программно инвертированный использование темного фона.|  
  
 **Источник**  
  
 \<Источника > элемент определяет один исходный ресурс изображения (XAML и PNG).  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**Attribute (XElement Dynamic Property)** (Attribute (динамическое свойство XElement))|**Определение**|  
|URI|[Обязательно] URI, который определяет, где можно загрузить изображение из. Он может принимать одно из следующих:<br /><br /> -A [пакет URI](http://msdn.microsoft.com/en-US/library/aa970069\(v=vs.100\).aspx) в приложении: / / / центр<br />-Ссылки на ресурс абсолютный компонента<br />— Путь к файлу, содержащему машинный ресурс|  
|Фон|[Необязательно] Указывает, что на вида фона источник предназначен для использования.<br /><br /> Он может принимать одно из следующих:<br /><br /> *Индикатор:* источник можно использовать на светлым фоном.<br /><br /> *Темная:*источник можно использовать на темного фона.<br /><br /> *Высокая контрастность:* источник можно использовать на любой фоне в режиме высокой контрастности.<br /><br /> *HighContrastLight:* источник можно использовать на светло-фоне в режиме высокой контрастности.<br /><br /> *HighContrastDark:* источник можно использовать на темного фона в режиме высокой контрастности.<br /><br /> Если опустить атрибут фона, источник можно использовать на любой фоне.<br /><br /> Если фон *свет*, *темной*, *HighContrastLight*, или *HighContrastDark*, никогда не инвертирования цветов источника. Если опущен или установлен фоновом режиме *Высокая контрастность*, управляет инверсия цветов источника изображения **AllowColorInversion** атрибута.|  
|||  
  
 Объект \<источника > элемент может иметь только один из следующих субэлементов необязательно:  
  
||||  
|-|-|-|  
|**Элемент**|**Атрибуты (все обязательные)**|**Определение**|  
|\<Размер >|Значение|Источник будет использоваться для образов определенного размера (в единицах устройства). Изображение будет квадрат.|  
|\<SizeRange >|MinSize MaxSize|Источник будет использован для образов из MinSize MaxSize (в единицах устройства) включительно. Изображение будет квадрат.|  
|\<Измерения >|Ширина, высота|Источник будет использоваться для образов заданную ширину и высоту (в единицах устройства).|  
|\<DimensionRange >|MinWidth MinHeight,<br /><br /> MaxWidth MaxHeight|Источник будет использован для образов из минимальную ширину и высоту для максимальной ширины или высоты (в единицах устройства) включительно.|  
  
 Объект \<источника > элемент может иметь дополнительный \<NativeResource > дочерний элемент, который определяет \<источника >, загружается из сборки в машинном коде, а не управляемой сборки.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**Attribute (XElement Dynamic Property)** (Attribute (динамическое свойство XElement))|**Определение**|  
|Тип|[Обязательно] Тип собственного ресурса, XAML или PNG|  
|ID|[Обязательно] Идентификатор целой части машинный ресурс|  
  
 **ImageList**  
  
 \<ImageList > элемент определяет коллекцию изображений, которые могут быть возвращены в одной ленты. Лента строится по требованию, при необходимости.  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|||  
|-|-|  
|**Attribute (XElement Dynamic Property)** (Attribute (динамическое свойство XElement))|**Определение**|  
|Guid|[Обязательно] GUID для моникер изображения|  
|ID|[Обязательно] Идентификатор часть моникер изображения|  
|Внешняя|[Необязательно, по умолчанию: false] Указывает, ссылается ли моникер изображения на изображение в текущий манифест.|  
  
 Моникер для автономной изображения нет ссылок на изображения, определенные в текущий манифест. Если автономной изображение не удается найти в библиотеке изображений, вместо него будет использоваться пустой местозаполнителя.  
  
## <a name="using-the-image-service"></a>С помощью службы изображений  
  
### <a name="first-steps-managed"></a>Первые шаги (управляемый код)  
 Использовать службу образа, необходимо добавить в проект ссылки на некоторые или все из следующих сборок:  
  
-   **Microsoft.VisualStudio.ImageCatalog.dll**  
  
    -   Требуется при использовании встроенного изображения каталога KnownMonikers  
  
-   **Microsoft.VisualStudio.Imaging.dll**  
  
    -   Является обязательным, если используется **CrispImage** и **ImageThemingUtilities** в пользовательский Интерфейс WPF  
  
-   **Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll**  
  
    -   Является обязательным, если используется **ImageMoniker** и **ImageAttributes** типы  
  
    -   **EmbedInteropTypes** должно быть задано значение true  
  
-   **Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime**  
  
    -   Является обязательным, если используется **IVsImageService2** типа  
  
    -   **EmbedInteropTypes** должно быть задано значение true  
  
-   **Microsoft.VisualStudio.Utilities.dll**  
  
    -   Является обязательным, если используется **BrushToColorConverter** для ImageThemingUtilities. **ImageBackgroundColor** в пользовательский Интерфейс WPF  
  
-   **Microsoft.VisualStudio.Shell. \<VSVersion >.0**  
  
    -   Является обязательным, если используется **IVsUIObject** типа  
  
-   **Microsoft.VisualStudio.Shell.Interop.10.0.dll**  
  
    -   Требуется при использовании пользовательского интерфейса, связанных с WinForms помощников  
  
    -   **EmbedInteropTypes** должно быть задано значение true  
  
### <a name="first-steps-native"></a>Первые шаги (машинный код)  
 Использовать службу образа, необходимо включить некоторые или все из следующих заголовков в проект:  
  
-   **KnownImageIds.h**  
  
    -   Требуется при использовании встроенного изображения каталога **KnownMonikers**, но не могут использоваться **ImageMoniker** типа, например когда возвращение значения из **IVsHierarchy GetGuidProperty**или **GetProperty** вызовов.  
  
-   **KnownMonikers.h**  
  
    -   Требуется при использовании встроенного изображения каталога **KnownMonikers**.  
  
-   **ImageParameters140.h**  
  
    -   Является обязательным, если используется **ImageMoniker** и **ImageAttributes** типов.  
  
-   **VSShell140.h**  
  
    -   Является обязательным, если используется **IVsImageService2** типа.  
  
-   **ImageThemingUtilities.h**  
  
    -   Требуется, если не удается разрешить служба образов в дескриптор темы.  
  
    -   Не используйте этот заголовок, если служба образов может обработать ваш изображения темы.  
  
-   **VSUIDPIHelper.h**  
  
    -   Требуется при использовании DPI вспомогательные методы для получения текущего точек на ДЮЙМ.  
  
## <a name="how-do-i-write-new-wpf-ui"></a>Как написать новый пользовательский Интерфейс WPF  
  
1.  Начните с добавления ссылки на сборки, необходимые в указанных выше начальные действия раздела в проект. Не нужно добавить все из них, так что добавьте ссылки, что нужно. (Примечание: Если вы используете или иметь доступ к **цвета** вместо **кисти**, то можно пропустить ссылку на **служебные программы**, поскольку не нужно преобразователь.)  
  
2.  Выберите нужный образ и получить его моникера. Используйте **KnownMoniker**, или использовать собственную при наличии собственных пользовательских образов и моникеры.  
  
3.  Добавить **CrispImages** в коде XAML. (См. ниже пример).  
  
4.  Задать **ImageThemingUtilities.ImageBackgroundColor** свойство в иерархии пользовательского интерфейса. (Это свойство должно быть значение там, где цвет фона известен, не обязательно в **CrispImage**.) (См. ниже пример).  
  
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
  
 **Как обновить существующие пользовательского интерфейса WPF?**  
  
 Обновление существующего пользовательского интерфейса WPF — относительно простой процесс, который состоит из трех основных этапов:  
  
1.  Заменить все \<изображение > элементов пользовательского интерфейса с \<CrispImage > элементов  
  
2.  Изменить все атрибуты исходного моникера атрибутов  
  
    -   Если изображение никогда не меняется, и вы используете **KnownMonikers**, статически связать свойства **KnownMoniker**. (См. приведенный выше пример).  
  
    -   Если вы используете собственное изображение изображение никогда не меняется, статически связать с собственного моникера.  
  
    -   Если изображения можно изменить, привязан атрибут моникер кода свойство, которое уведомляет об изменениях свойств.  
  
3.  Где-нибудь в иерархии пользовательского интерфейса, установите **ImageThemingUtilities.ImageBackgroundColor** чтобы убедиться, что цветовой инверсии работает правильно.  
  
    -   Это может потребовать использования **BrushToColorConverter** класса. (См. приведенный выше пример).  
  
## <a name="how-do-i-update-win32-ui"></a>Как обновить пользовательский Интерфейс Win32?  
 Добавьте следующий код, везде, где следует заменить необработанные загрузку образов. Переключение значений для возвращения HBITMAP и HICONs и HIMAGELIST при необходимости.  
  
 **Служба изображений**  
  
```cpp  
CComPtr<IVsImageService2> spImgSvc;  
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);  
```  
  
 **Запрос образа**  
  
```cpp  
ImageAttributes attr = { 0 };  
attr.StructSize      = sizeof(attributes);  
attr.Format          = DF_Win32;  
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST  
attr.ImageType       = IT_Bitmap;  
attr.LogicalWidth    = 16;  
attr.LogicalHeight   = 16;  
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();  
attr.Background      = 0xFFFFFFFF;  
// Desired RGBA color, if you don't use this, don't set IAF_Background below  
attr.Flags           = IAF_RequiredFlags | IAF_Background;  
  
CComPtr<IVsUIObject> spImg;  
// Replace this KnownMoniker with your desired ImageMoniker  
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);  
  
```  
  
## <a name="how-do-i-update-winforms-ui"></a>Как обновить WinForms пользовательского интерфейса?  
 Добавьте следующий код, везде, где следует заменить необработанные загрузку образов. Переключение значений для возвращения точечных рисунков и значков, при необходимости.  
  
 **Полезными, с помощью инструкции**  
  
```csharp  
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;  
```  
  
 **Служба изображений**  
  
```csharp  
// This or your preferred way of querying for Visual Studio services  
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));  
  
```  
  
 **Запрос изображения**  
  
```csharp  
ImageAttributes attributes = new ImageAttributes  
{  
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),  
    // IT_Bitmap for Bitmap, IT_Icon for Icon  
    ImageType     = (uint)_UIImageType.IT_Bitmap,  
    Format        = (uint)_UIDataFormat.DF_WinForms,  
    LogicalWidth  = 16,  
    LogicalHeight = 16,  
    // Desired RGBA color, if you don't use this, don't set IAF_Background below  
    Background    = 0xFFFFFFFF,  
    Flags = (uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background,  
};  
  
// Replace this KnownMoniker with your desired ImageMoniker  
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);  
  
Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap  
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj); // Use this if you need an icon  
  
```  
  
## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Использование моникеров изображение в новое окно инструментов  
 Шаблон проекта пакета VSIX был обновлен для Visual Studio 2015. Чтобы создать новое окно инструментов, правой кнопкой мыши проект VSIX и выберите «Добавить новый элемент...» (Сочетание клавиш Ctrl + Shift + A). В узле расширения языка проекта выберите «Пользовательский инструмент окно» введите имя в окне инструментов и нажмите кнопку «Добавить».  
  
 Это ключевой разрядов, используемое моникеров в окне инструментов. Следуйте инструкциям для каждого.  
  
1.  Вкладка окна инструментов, когда вкладки получить небольшой достаточно (также используемый в переключателе окна Ctrl + Tab).  
  
     Добавьте следующую строку в конструктор для класса, производного от **ToolWindowPane** типа:  
  
    ```csharp  
    // Replace this KnownMoniker with your desired ImageMoniker  
    this.BitmapImageMoniker = KnownMonikers.Blank;  
    ```  
  
2.  Команда, чтобы открыть окно инструментов.  
  
     В vsct-файле для пакета измените в окне инструментов кнопки:  
  
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
  
 **Использование моникеров изображения в существующее окно инструментов**  
  
 Обновление существующему окну инструмента использование моникеров образа аналогичен действия по созданию нового окна средства.  
  
 Это ключевой разрядов, используемое моникеров в окне инструментов. Следуйте инструкциям для каждого.  
  
1.  Вкладка окна инструментов, когда вкладки получить небольшой достаточно (также используемый в переключателе окна Ctrl + Tab).  
  
    1.  Удалить эти строки (если они существуют) в конструктор для класса, производного от **ToolWindowPane** типа:  
  
        ```csharp  
        this.BitmapResourceID = <Value>;  
        this.BitmapIndex = <Value>;  
        ```  
  
    2.  Шаг #1. в разделе «Как? использование моникеров изображения в новом окне средства» раздел выше.  
  
2.  Команда, чтобы открыть окно инструментов.  
  
    -   Шаг #2. в разделе «Как? использование моникеров изображения в новом окне средства» раздел выше.  
  
## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Использование моникеров изображения в vsct-файл  
 Обновление vsct-файл, как указано в комментарии ниже строки:  
  
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
  
 **Что делать, если в vsct-файл также необходимо прочитать в более ранних версиях Visual Studio?**  
  
 Более ранние версии Visual Studio не распознают **IconIsMoniker** команда флаг. Можно использовать образы из служба образов в версиях Visual Studio, которые поддерживают его, но продолжать использовать старый стиль изображения в предыдущих версиях Visual Studio. Чтобы сделать это, будет оставьте vsct-файл без изменений (и поэтому совместимость с более ранними версиями Visual Studio) и создать файл CSV (значения с разделителями запятыми), сопоставляемый с пары GUID или идентификатор, определенные в vsct-файл \<точечные рисунки > элемента изображения моникер пары GUID-идентификатор.  
  
 Имеет формат CSV-файла сопоставления:  
  
```  
Icon guid, Icon id, Moniker guid, Moniker id  
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100  
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200  
```  
  
 CSV-файл развертывается в пакете и его расположение задается **IconMappingFilename** свойство **ProvideMenuResource** атрибут пакета:  
  
```csharp  
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]  
```  
  
 **IconMappingFilename** относительный путь неявно выходящую $PackageFolder$ (как показано в примере выше) или абсолютный путь явно корнем в каталог, определенный параметром переменной среды, например @"%UserProfile%\ dir1\dir2\MyMappingFile.csv».  
  
## <a name="how-do-i-port-a-project-system"></a>Как перенести систему проектов?  
 **Как предоставить ImageMonikers для проекта**  
  
1.  Реализуйте **VSHPROPID_SupportsIconMonikers** в проекте **IVsHierarchy**и возвращает значение true.  
  
2.  Реализации **VSHPROPID_IconMonikerImageList** (при использовании в исходном проекте **VSHPROPID_IconImgList**) или **VSHPROPID_IconMonikerGuid**,  **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (при использовании в исходном проекте  **VSHPROPID_IconHandle** и **VSHPROPID_OpenFolderIconHandle**).  
  
3.  Измените реализацию исходного VSHPROPIDs для значков для создания «устаревшего» версий значки, если их запрашивают точек расширения. **IVsImageService2** предоставляет функциональные возможности, необходимые для получения этих значков  
  
 **Дополнительные требования для VB / C# разновидности**  
  
 Реализовать только **VSHPROPID_SupportsIconMonikers** при обнаружении, что проект является **внешней flavor**. В противном случае фактический внешний flavor могут не поддерживать моникеров изображения на самом деле и вашей базовой версии могут эффективно «скрыть» настроенных образов.  
  
 **Использование моникеров изображения в CPS**  
  
 Задание пользовательских образов в CPS (общая система проектов) можно сделать вручную или с помощью шаблона элемента, входящий в состав пакета SDK для расширения системы проекта.  
  
 **Используя пакет SDK для расширения системы проектов**  
  
 Следуйте инструкциям в [использовать настраиваемые значки для типа элемента типа проекта](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) для настройки CPS изображений. Дополнительные сведения о CPS можно найти в [документации системы расширяемости Visual Studio проекта](https://github.com/Microsoft/VSProjectSystem)  
  
 **Можно вручную настроить ImageMonikers**  
  
1.  Реализация и экспортировать **IProjectTreeModifier** интерфейса в своей системе проектов.  
  
2.  Определите, какой **KnownMoniker** или вы хотите использовать специальное имя пользовательского образа.  
  
3.  В **ApplyModifications** метод, выполните следующие действия в любом месте метод перед возвратом нового дерева, аналогично ниже примере:  
  
    ```csharp  
    // Replace this KnownMoniker with your desired ImageMoniker  
    tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());  
    ```  
  
4.  При создании нового дерева, можно задать пользовательские изображения путем передачи в метод NewTree аналогично требуемой моникеров ниже примере:  
  
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
  
## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Как преобразовать из реальных изображений на основе моникера изображений?  
 **Требуется ли поддержка HIMAGELISTs**  
  
 При наличии существующих изображений для кода, необходимо обновить для использования службы изображения, но ограничены API, которые требуют передачи списков изображений можно получить преимущества службы изображения. Чтобы создать изображений на основе моникера, выполните следующие действия, чтобы создать манифест с существующие моникеры.  
  
1.  Запустите **ManifestFromResources** средство, передавая ему набора изображений. Создает манифест для полосе.  
  
    -   Рекомендуется: укажите имя не по умолчанию для манифеста в соответствии с его использования.  
  
2.  Если вы используете только **KnownMonikers**, затем выполните следующие действия:  
  
    -   Замените \<изображения > раздел манифеста с \<изображения / >.  
  
    -   Удалите все идентификаторы subimage (что-либо с \<имя imagestrip > _ ##).  
  
    -   Рекомендуется: переименуйте символ AssetsGuid и символ полосы изображения в соответствии с его использования.  
  
    -   Замените каждый **ContainedImage**GUID $ (ImageCatalogGuid), замените каждый **ContainedImage**в код с помощью $(\<моникер >) и добавьте атрибут внешних = «true» для каждого **ContainedImage**  
  
        -   \<моникер > должно быть заменено **KnownMoniker** , совпадал с образом, но с «KnownMonikers». удалены из имени.  
  
    -   Добавить < Manifest="$(ManifestFolder) импорта\\< dir путь для установки относительно\>\Microsoft.VisualStudio.ImageCatalog.imagemanifest» /\> в верхнюю часть \<символы > раздела.  
  
        -   Относительный путь определяется местоположение развертывания, определенные в программе установки, создания манифеста.  
  
3.  Запустите **ManifestToCode** средства для создания программы-оболочки, чтобы существующий код имеет специальное имя, его можно использовать для запроса к службе образа для набора изображений.  
  
    -   Рекомендуется: задайте имена не по умолчанию для программы-оболочки и пространства имен в соответствии с их использованием.  
  
4.  Выполните все добавляет, разработки и развертывания и установки и другие изменения кода для работы со службой изображения и новые файлы.  
  
 Пример манифеста, включая внутренние и внешние изображения, чтобы увидеть, оно должно иметь вид:  
  
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
  
 **Нет необходимости поддерживать HIMAGELISTs**  
  
1.  Определить набор **KnownMonikers** , соответствует изображений в вашей изображений, или создать собственные моникеров для образов в вашей изображений.  
  
2.  Обновите любые сопоставление используется для получения изображения по индексу требуется набора изображений, вместо этого использовать специальные имена.  
  
3.  Обновите код, чтобы используют службу образов для запроса моникеров через обновленные сопоставления. (Это может означать обновление для **CrispImages** для управляемого кода, или запрос HBITMAP или HICONs из службы образов в и передача их вокруг для машинного кода.)  
  
## <a name="testing-your-images"></a>Тестирование изображения  
 Средство просмотра библиотеки изображений можно использовать для тестирования манифесты изображения, чтобы убедиться в том, что все, что создан правильно. Можно найти средство в [пакет SDK для Visual Studio 2015](http://msdn.microsoft.com/library/bb166441.aspx). Можно найти документацию по этой и другими инструментами [здесь](http://aka.ms/VSImageThemeTools).  
  
## <a name="additional-resources"></a>Дополнительные ресурсы  
  
### <a name="samples"></a>Примеры  
 Некоторые примеры Visual Studio на сайте GitHub были обновлены для использования службы образов в составе разных точках расширяемости Visual Studio.  
  
 Проверьте [http://github.com/Microsoft/VSSDK-Extensibility-Samples](http://github.com/Microsoft/VSSDK-Extensibility-Samples) для самые свежие образцы.  
  
### <a name="tooling"></a>Инструментарий  
 Набор средств поддержки службы образов был создан для помощи в создании или обновлении пользовательский Интерфейс, который работает со службой изображения. Дополнительные сведения о каждом инструменте см. в документации, поставляемой с этими средствами. Средства будут включены в [пакет SDK для Visual Studio 2015.](http://msdn.microsoft.com/library/bb166441.aspx)  
  
 **ManifestFromResources**  
  
 Манифест из ресурсов средство принимает список ресурсов изображений (PNG или XAML) и создает файл манифеста изображения для использования этих образов служба образов.  
  
 **ManifestToCode**  
  
 Манифест, чтобы средство кода принимает файл манифеста изображения и создает файл-оболочки для ссылок на манифеста значения в коде (C++, C# или VB) или в vsct-файлами.  
  
 **ImageLibraryViewer**  
  
 Средство просмотра библиотеки изображений может загружать манифестов изображений и позволяет пользователю управлять ими таким же образом, что Visual Studio, чтобы убедиться в том, что манифест создан правильно. Пользователь может изменить фон, размеры, параметр DPI, высокая контрастность и другие параметры. Также отображает сведения о загрузке для поиска ошибок в манифестах и отображает сведения об источнике для каждого изображения в манифесте.  
  
## <a name="faq"></a>часто задаваемые вопросы  
  
-   Существуют ли все зависимости, которые необходимо включить при загрузке \<Include="Microsoft.VisualStudio.* ссылки. Interop.14.0.DesignTime» / >?  
  
    -   Задать EmbedInteropTypes = «true» на все библиотеки DLL взаимодействия.  
  
-   Развертывание файла манифеста образа с расширением my  
  
    -   Добавьте файл .imagemanifest в проект.  
  
    -   Задайте для параметра «Включить в VSIX» значение True.  
  
-   Обновлении CPS системы проекта. Что произошло с **ImageName** и **StockIconService**?  
  
    -   o, они были удалены при CPS был изменен для использования специальных имен. Больше не требуется вызывать **StockIconService**, просто передайте нужный **KnownMoniker** метода или свойства с помощью **ToProjectSystemType()** метод расширения в средства CPS. Можно найти сопоставление **ImageName** для **KnownMonikers** ниже:  
  
        |||  
        |-|-|  
        |**ImageName**|**KnownMoniker**|  
        |ImageName.OfflineWebApp|KnownImageIds.Web|  
        |ImageName.WebReferencesFolder|KnownImageIds.Web|  
        |ImageName.OpenReferenceFolder|KnownImageIds.FolderOpened|  
        |ImageName.ReferenceFolder|KnownImageIds.Reference|  
        |ImageName.Reference|KnownImageIds.Reference|  
        |ImageName.SdlWebReference|KnownImageIds.WebReferenceFolder|  
        |ImageName.DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|  
        |ImageName.Folder|KnownImageIds.FolderClosed|  
        |ImageName.OpenFolder|KnownImageIds.FolderOpened|  
        |ImageName.ExcludedFolder|KnownImageIds.HiddenFolderClosed|  
        |ImageName.OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|  
        |ImageName.ExcludedFile|KnownImageIds.HiddenFile|  
        |ImageName.DependentFile|KnownImageIds.GenerateFile|  
        |ImageName.MissingFile|KnownImageIds.DocumentWarning|  
        |ImageName.WindowsForm|KnownImageIds.WindowsForm|  
        |ImageName.WindowsUserControl|KnownImageIds.UserControl|  
        |ImageName.WindowsComponent|KnownImageIds.ComponentFile|  
        |ImageName.XmlSchema|KnownImageIds.XMLSchema|  
        |ImageName.XmlFile|KnownImageIds.XMLFile|  
        |ImageName.WebForm|KnownImageIds.Web|  
        |ImageName.WebService|KnownImageIds.WebService|  
        |ImageName.WebUserControl|KnownImageIds.WebUserControl|  
        |ImageName.WebCustomUserControl|KnownImageIds.WebCustomControl|  
        |ImageName.AspPage|KnownImageIds.ASPFile|  
        |ImageName.GlobalApplicationClass|KnownImageIds.SettingsFile|  
        |ImageName.WebConfig|KnownImageIds.ConfigurationFile|  
        |ImageName.HtmlPage|KnownImageIds.HTMLFile|  
        |ImageName.StyleSheet|KnownImageIds.StyleSheet|  
        |ImageName.ScriptFile|KnownImageIds.JSScript|  
        |ImageName.TextFile|KnownImageIds.Document|  
        |ImageName.SettingsFile|KnownImageIds.Settings|  
        |ImageName.Resources|KnownImageIds.DocumentGroup|  
        |ImageName.Bitmap|KnownImageIds.Image|  
        |ImageName.Icon|KnownImageIds.IconFile|  
        |ImageName.Image|KnownImageIds.Image|  
        |ImageName.ImageMap|KnownImageIds.ImageMapFile|  
        |ImageName.XWorld|KnownImageIds.XWorldFile|  
        |ImageName.Audio|KnownImageIds.Sound|  
        |ImageName.Video|KnownImageIds.Media|  
        |ImageName.Cab|KnownImageIds.CABProject|  
        |ImageName.Jar|KnownImageIds.JARFile|  
        |ImageName.DataEnvironment|KnownImageIds.DataTable|  
        |ImageName.PreviewFile|KnownImageIds.Report|  
        |ImageName.DanglingReference|KnownImageIds.ReferenceWarning|  
        |ImageName.XsltFile|KnownImageIds.XSLTransform|  
        |ImageName.Cursor|KnownImageIds.CursorFile|  
        |ImageName.AppDesignerFolder|KnownImageIds.Property|  
        |ImageName.Data|KnownImageIds.Database|  
        |ImageName.Application|KnownImageIds.Application|  
        |ImageName.DataSet|KnownImageIds.DatabaseGroup|  
        |ImageName.Pfx|KnownImageIds.Certificate|  
        |ImageName.Snk|KnownImageIds.Rule|  
        |ImageName.VisualBasicProject|KnownImageIds.VBProjectNode|  
        |ImageName.CSharpProject|KnownImageIds.CSProjectNode|  
        |ImageName.Empty|KnownImageIds.Blank|  
        |ImageName.MissingFolder|KnownImageIds.FolderOffline|  
        |ImageName.SharedImportReference|KnownImageIds.SharedProject|  
        |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|  
        |ImageName.SharedProjectVc|KnownImageIds.CPPSharedProject|  
        |ImageName.SharedProjectJs|KnownImageIds.JSSharedProject|  
        |ImageName.CSharpCodeFile|KnownImageIds.CSFileNode|  
        |ImageName.VisualBasicCodeFile|KnownImageIds.VBFileNode|  
  
    -   Обновлении Мой поставщик списка завершения. Что **KnownMonikers** соответствует к старой **StandardGlyphGroup** и **StandardGlyph** значений?  
  
        ||||  
        |-|-|-|  
        |GlyphGroupClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupConstant|GlyphItemPublic|ClassPublic|  
        |GlyphGroupConstant|GlyphItemInternal|ClassInternal|  
        |GlyphGroupConstant|GlyphItemFriend|ClassInternal|  
        |GlyphGroupConstant|GlyphItemProtected|ClassProtected|  
        |GlyphGroupConstant|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupConstant|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|  
        |GlyphGroupDelegate|GlyphItemInternal|DelegateInternal|  
        |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|  
        |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|  
        |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|  
        |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|  
        |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|  
        |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal|  
        |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal|  
        |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|  
        |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|  
        |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|  
        |GlyphGroupEnumMember|GlyphItemPublic|EnumerationMemberPublic|  
        |GlyphGroupEnumMember|GlyphItemInternal|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemFriend|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemProtected|EnumerationMemberProtected|  
        |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationMemberPrivate|  
        |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationMemberShortcut|  
        |GlyphGroupEvent|GlyphItemPublic|EventPublic|  
        |GlyphGroupEvent|GlyphItemInternal|EventInternal|  
        |GlyphGroupEvent|GlyphItemFriend|EventInternal|  
        |GlyphGroupEvent|GlyphItemProtected|EventProtected|  
        |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|  
        |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|  
        |GlyphGroupException|GlyphItemPublic|ExceptionPublic|  
        |GlyphGroupException|GlyphItemInternal|ExceptionInternal|  
        |GlyphGroupException|GlyphItemFriend|ExceptionInternal|  
        |GlyphGroupException|GlyphItemProtected|ExceptionProtected|  
        |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|  
        |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|  
        |GlyphGroupField|GlyphItemPublic|FieldPublic|  
        |GlyphGroupField|GlyphItemInternal|FieldInternal|  
        |GlyphGroupField|GlyphItemFriend|FieldInternal|  
        |GlyphGroupField|GlyphItemProtected|FieldProtected|  
        |GlyphGroupField|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupField|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|  
        |GlyphGroupInterface|GlyphItemInternal|InterfaceInternal|  
        |GlyphGroupInterface|GlyphItemFriend|InterfaceInternal|  
        |GlyphGroupInterface|GlyphItemProtected|InterfaceProtected|  
        |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|  
        |GlyphGroupInterface|GlyphItemShortcut|InterfaceShortcut|  
        |GlyphGroupMacro|GlyphItemPublic|MacroPublic|  
        |GlyphGroupMacro|GlyphItemInternal|MacroInternal|  
        |GlyphGroupMacro|GlyphItemFriend|MacroInternal|  
        |GlyphGroupMacro|GlyphItemProtected|MacroProtected|  
        |GlyphGroupMacro|GlyphItemPrivate|MacroPrivate|  
        |GlyphGroupMacro|GlyphItemShortcut|MacroShortcut|  
        |GlyphGroupMap|GlyphItemPublic|MapPublic|  
        |GlyphGroupMap|GlyphItemInternal|MapInternal|  
        |GlyphGroupMap|GlyphItemFriend|MapInternal|  
        |GlyphGroupMap|GlyphItemProtected|MapProtected|  
        |GlyphGroupMap|GlyphItemPrivate|MapPrivate|  
        |GlyphGroupMap|GlyphItemShortcut|MapShortcut|  
        |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|  
        |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|  
        |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|  
        |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|  
        |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|  
        |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|  
        |GlyphGroupMethod|GlyphItemPublic|MethodPublic|  
        |GlyphGroupMethod|GlyphItemInternal|MethodInternal|  
        |GlyphGroupMethod|GlyphItemFriend|MethodInternal|  
        |GlyphGroupMethod|GlyphItemProtected|MethodProtected|  
        |GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupMethod|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupOverload|GlyphItemPublic|MethodPublic|  
        |GlyphGroupOverload|GlyphItemInternal|MethodInternal|  
        |GlyphGroupOverload|GlyphItemFriend|MethodInternal|  
        |GlyphGroupOverload|GlyphItemProtected|MethodProtected|  
        |GlyphGroupOverload|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupModule|GlyphItemPublic|ModulePublic|  
        |GlyphGroupModule|GlyphItemInternal|ModuleInternal|  
        |GlyphGroupModule|GlyphItemFriend|ModuleInternal|  
        |GlyphGroupModule|GlyphItemProtected|ModuleProtected|  
        |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|  
        |GlyphGroupModule|GlyphItemShortcut|ModuleShortcut|  
        |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|  
        |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|  
        |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|  
        |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|  
        |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|  
        |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|  
        |GlyphGroupOperator|GlyphItemPublic|OperatorPublic|  
        |GlyphGroupOperator|GlyphItemInternal|OperatorInternal|  
        |GlyphGroupOperator|GlyphItemFriend|OperatorInternal|  
        |GlyphGroupOperator|GlyphItemProtected|OperatorProtected|  
        |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|  
        |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut|  
        |GlyphGroupProperty|GlyphItemPublic|PropertyPublic|  
        |GlyphGroupProperty|GlyphItemInternal|PropertyInternal|  
        |GlyphGroupProperty|GlyphItemFriend|PropertyInternal|  
        |GlyphGroupProperty|GlyphItemProtected|PropertyProtected|  
        |GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|  
        |GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|  
        |GlyphGroupStruct|GlyphItemPublic|StructurePublic|  
        |GlyphGroupStruct|GlyphItemInternal|StructureInternal|  
        |GlyphGroupStruct|GlyphItemFriend|StructureInternal|  
        |GlyphGroupStruct|GlyphItemProtected|StructureProtected|  
        |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|  
        |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut|  
        |GlyphGroupTemplate|GlyphItemPublic|TemplatePublic|  
        |GlyphGroupTemplate|GlyphItemInternal|TemplateInternal|  
        |GlyphGroupTemplate|GlyphItemFriend|TemplateInternal|  
        |GlyphGroupTemplate|GlyphItemProtected|TemplateProtected|  
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
        |GlyphGroupType|GlyphItemProtected|TypeProtected|  
        |GlyphGroupType|GlyphItemPrivate|TypePrivate|  
        |GlyphGroupType|GlyphItemShortcut|TypeShortcut|  
        |GlyphGroupUnion|GlyphItemPublic|UnionPublic|  
        |GlyphGroupUnion|GlyphItemInternal|UnionInternal|  
        |GlyphGroupUnion|GlyphItemFriend|UnionInternal|  
        |GlyphGroupUnion|GlyphItemProtected|UnionProtected|  
        |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|  
        |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|  
        |GlyphGroupVariable|GlyphItemPublic|FieldPublic|  
        |GlyphGroupVariable|GlyphItemInternal|FieldInternal|  
        |GlyphGroupVariable|GlyphItemFriend|FieldInternal|  
        |GlyphGroupVariable|GlyphItemProtected|FieldProtected|  
        |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|  
        |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|  
        |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|  
        |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|  
        |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|  
        |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|  
        |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|  
        |GlyphGroupIntrinsic|GlyphItemInternal|ObjectInternal|  
        |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|  
        |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|  
        |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|  
        |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|  
        |GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|  
        |GlyphGroupJSharpMethod|GlyphItemInternal|MethodInternal|  
        |GlyphGroupJSharpMethod|GlyphItemFriend|MethodInternal|  
        |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|  
        |GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|  
        |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal|  
        |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|  
        |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|  
        |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupJSharpClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupJSharpClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|  
        |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|  
        |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|  
        |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|  
        |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|  
        |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|  
        |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|  
        |GlyphGroupJSharpInterface|GlyphItemInternal|InterfaceInternal|  
        |GlyphGroupJSharpInterface|GlyphItemFriend|InterfaceInternal|  
        |GlyphGroupJSharpInterface|GlyphItemProtected|InterfaceProtected|  
        |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|  
        |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|  
        |GlyphGroupError||StatusError|  
        |GlyphBscFile||ClassFile|  
        |GlyphAssembly||Ссылка|  
        |GlyphLibrary||Библиотека|  
        |GlyphVBProject||VBProjectNode|  
        |GlyphCoolProject||CSProjectNode|  
        |GlyphCppProject||CPPProjectNode|  
        |GlyphDialogId||Диалоговое окно|  
        |GlyphOpenFolder||FolderOpened|  
        |GlyphClosedFolder||FolderClosed|  
        |GlyphArrow||GoToNext|  
        |GlyphCSharpFile||CSFileNode|  
        |GlyphCSharpExpansion||Фрагмент кода|  
        |GlyphKeyword||IntellisenseKeyword|  
        |GlyphInformation||StatusInformation|  
        |GlyphReference||ClassMethodReference|  
        |GlyphRecursion||Рекурсия|  
        |GlyphXmlItem||Тег|  
        |GlyphJSharpProject||DocumentCollection|  
        |GlyphJSharpDocument||Document|  
        |GlyphForwardType||GoToNext|  
        |GlyphCallersGraph||Использованием CallTo|  
        |GlyphCallGraph||CallFrom|  
        |GlyphWarning||StatusWarning|  
        |GlyphMaybeReference||QuestionMark|  
        |GlyphMaybeCaller||Использованием CallTo|  
        |GlyphMaybeCall||CallFrom|  
        |GlyphExtensionMethod||ExtensionMethod|  
        |GlyphExtensionMethodInternal||ExtensionMethod|  
        |GlyphExtensionMethodFriend||ExtensionMethod|  
        |GlyphExtensionMethodProtected||ExtensionMethod|  
        |GlyphExtensionMethodPrivate||ExtensionMethod|  
        |GlyphExtensionMethodShortcut||ExtensionMethod|  
        |GlyphXmlAttribute||XmlAttribute|  
        |GlyphXmlChild||XmlElement|  
        |GlyphXmlDescendant||XmlDescendant|  
        |GlyphXmlNamespace||XmlNamespace|  
        |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|  
        |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|  
        |GlyphXmlChildQuestion||XmlElementLowConfidence|  
        |GlyphXmlChildCheck||XmlElementHighConfidence|  
        |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|  
        |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|  
        |GlyphCompletionWarning||IntellisenseWarning|