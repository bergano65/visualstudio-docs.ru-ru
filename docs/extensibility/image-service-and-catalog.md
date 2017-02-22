---
title: "Служба образов и каталога | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
caps.latest.revision: 37
caps.handback.revision: 37
ms.author: "gregvanl"
manager: "ghogen"
---
# Служба образов и каталога
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Это руководство содержит инструкции и рекомендации по внедрению службы изображений Visual Studio и каталог образа, представленные в Visual Studio 2015.  
  
 Служба образов, представленные в Visual Studio 2015 позволяет разработчикам получить лучший изображения для устройства и пользователя выбранная тема для отображения изображения, включая правильный темы для контекста, в котором они отображаются. Внедрение служба образов позволит избежать основных болевые точки, связанные с средства обслуживания, HDPI масштабирования и темы.  
  
|||  
|-|-|  
|**Сегодня проблем**|**Решения**|  
|Наложение цвета фона|Встроенные альфа-смешение|  
|Образы темы (некоторые)|Метаданные темы|  
|Режим высокой контрастности|Альтернативные ресурсы высокой контрастности|  
|Требуется несколько ресурсов для различных режимов точек на ДЮЙМ|Для выбора ресурсов с помощью векторной резервной|  
|Дублирующихся изображений|Один идентификатор каждого образа концепция|  
  
 Почему внедрять служба образов?  
  
-   Всегда получите последний образ «пикселей идеальное» из Visual Studio  
  
-   Можно передать и использовать собственные образы  
  
-   Не нужно проверять, если операционная система Windows добавляет новый масштабирование изображений  
  
-   Адрес старой архитектуры препятствий в реализации  
  
 Оболочка Visual Studio инструментов до и после применения образа службы:  
  
 ![Служба изображений "до" и "после"](../extensibility/media/image-service-before-and-after.png "Image Service Before and After")  
  
## <a name="how-it-works"></a>Принцип работы  
 Служба образов может предоставить растровый рисунок, подходящий для любой поддерживаемой платформы пользовательского интерфейса:  
  
-   WPF: BitmapSource  
  
-   WinForms: System.Drawing.Bitmap  
  
-   Win32: HBITMAP  
  
 Диаграмма потока службы изображения  
  
 ![Схема потока службы изображений](../extensibility/media/image-service-flow-diagram.png "Image Service Flow Diagram")  
  
 **Моникеры изображения**  
  
 Моникер изображения (или моникера для краткости) является парой или идентификатора GUID, однозначно определяющий ресурс изображения или изображения список активов в библиотеке изображений.  
  
 **Известные моникеров**  
  
 Набор моникеров изображения, содержащиеся в каталог образа Visual Studio и открыто может быть использован любой компонент Visual Studio или расширение.  
  
 **Файлы манифеста изображений**  
  
 Файлы манифеста (.imagemanifest) изображений, XML-файлы, которые определяют набор графических ресурсов, специальные имена, представляющие эти ресурсы и реального изображения или изображения, представляющие каждого ресурса. Манифесты изображения можно определить автономных образов или списки изображений для поддержки устаревшего кода пользовательского интерфейса. Кроме того существуют атрибуты, которые могут быть установлены на ресурс или на отдельных изображений за каждый актив Чтобы изменить условия и способ отображения этих ресурсов.  
  
 **Схема манифеста изображения**  
  
 Полный образ манифест выглядит следующим образом:  
  
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
  
 Как помочь читаемость и обслуживания, манифест изображения можно использовать символы для значений атрибутов. Символы, которые определены следующим образом:  
  
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
|Импорт|Импортирует символов из заданного файла манифеста для использования в текущий манифест|  
|Guid|Символ представляет собой идентификатор GUID и должно соответствовать форматирование GUID|  
|Идентификатор|Символ представляет идентификатор и должно быть неотрицательное целое число|  
|Строка|Произвольное строковое значение представляет символ|  
  
 Символы учитывается регистр, на который ссылаются, используя синтаксис $(symbol-name):  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 Некоторые символы являются стандартными для всех манифестов. Они могут использоваться в Uri атрибут \< источника> или \< Import> элемент пути для ссылок на локальном компьютере.  
  
|||  
|-|-|  
|**Символ**|**Описание**|  
|CommonProgramFiles|Значение переменной среды % CommonProgramFiles %|  
|LocalAppData|Значение переменной среды % LocalAppData %|  
|ManifestFolder|Папка, содержащая файл манифеста|  
|Мои документы|Полный путь папки "Мои документы" текущего пользователя|  
|ProgramFiles|Значение переменной среды % ProgramFiles %|  
|System|В папку Windows\System32|  
|WinDir|Значение переменной среды % WinDir %|  
  
 **Изображение**  
  
 \< Изображение> элемент определяет образ, который может ссылаться моникера. GUID и идентификатор, в совокупности формируют моникер изображения. Моникер для изображения должно быть уникальным для всего изображения библиотеки. Если более одного изображения данного моникера, возникла при построении библиотеки первый из них — тот, который сохраняется.  
  
 Он должен содержать хотя бы один источник. Зависящий от размера источников дает лучшие результаты широкого ряда размеры, но они не требуются. Если служба получает запрос на изображение размером не определены в \< изображение> элемента и не указан источник зависящий от размера, служба будет выбрать лучший источник определенного размера и масштабировать его до необходимого размера.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**Атрибут**|**Определение**|  
|Guid|[Required] GUID для специального имени образа|  
|Идентификатор|[Required] Идентификатор часть моникер изображения|  
|AllowColorInversion|[Необязательно, по умолчанию true] Указывает, имеют ли изображение его цвета программно инвертированного использование темного фона.|  
  
 **Источник**  
  
 \< Источник> элемент определяет один исходный ресурс изображения (XAML и PNG).  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**Атрибут**|**Определение**|  
|URI|[Required] URI, который определяет, где можно загрузить изображение из. Это может быть одно из следующих:<br /><br /> -A [пакет URI](http://msdn.microsoft.com/en-US/library/aa970069\(v=vs.100\).aspx) с помощью приложения: / / / центр<br />-Ссылки на ресурс абсолютный компоненты<br />— Путь к файлу, содержащему машинный ресурс|  
|Фон|[Необязательно] Указывает, что для типа источника планируется использовать фоновый рисунок.<br /><br /> Это может быть одно из следующих:<br /><br /> *Индикатор:* источник можно использовать на светло-фон.<br /><br /> *Темная:*источник можно использовать на темного фона.<br /><br /> *Высокая контрастность:* источник можно использовать на любой фона в режиме высокой контрастности.<br /><br /> *HighContrastLight:* источник можно использовать на светло-фон в режиме высокой контрастности.<br /><br /> *HighContrastDark:* источник можно использовать на темного фона в режиме высокой контрастности.<br /><br /> Если опустить атрибут фона, источник можно использовать на любой фоне.<br /><br /> Если фон *свет*, *темной*, *HighContrastLight*, или *HighContrastDark*, никогда не инвертированы исходного цвета. Если опущен или установлен фоновом режиме *Высокая контрастность*, управляет инверсия цветов исходного изображения **AllowColorInversion** атрибута.|  
|||  
  
 Объект \< источника> элемент может иметь только один из следующих подэлементов необязательно:  
  
||||  
|-|-|-|  
|**Элемент**|**Атрибуты (все обязательные)**|**Определение**|  
|\< размер>|Значение|Источник будет использоваться для изображений определенного размера (в единицах устройства). Изображение будет квадрата.|  
|\< SizeRange>|MinSize MaxSize|Будет использоваться источник для образов из MinSize MaxSize (в единицах устройства) включительно. Изображение будет квадрата.|  
|\< измерений>|Ширина, высота|Источник будет использоваться для образов заданную ширину и высоту (в единицах устройства).|  
|\< DimensionRange>|MinWidth MinHeight,<br /><br /> MaxWidth MaxHeight|Будет использоваться источник для образов из минимальную ширину и высоту в максимальной ширины или высоты (в единицах устройства) включительно.|  
  
 Объект \< источника> элемент может иметь необязательное \< NativeResource> дочерний элемент, который определяет \< источника> загруженный из сборки в машинном коде, а не управляемую сборку.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**Атрибут**|**Определение**|  
|Тип|[Required] Тип машинный ресурс, XAML или PNG|  
|Идентификатор|[Required] Идентификатор целой части машинный ресурс|  
  
 **ImageList**  
  
 \< ImageList> элемент определяет коллекцию изображений, которые могут быть возвращены в одной области. Лента строится по требованию, при необходимости.  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|||  
|-|-|  
|**Атрибут**|**Определение**|  
|Guid|[Required] GUID для специального имени образа|  
|Идентификатор|[Required] Идентификатор часть моникер изображения|  
|Внешнее|[Необязательно, по умолчанию-false] Указывает ли изображение моникер ссылается на изображение в текущий манифест.|  
  
 Моникер для изображения, содержащегося не должно ссылаться на определенные в манифесте текущего изображения. Если не удается найти изображения, содержащиеся в библиотеке изображений, пустой замещающее изображение будет использоваться на его месте.  
  
## <a name="using-the-image-service"></a>С помощью службы изображения  
  
### <a name="first-steps-managed"></a>Первые шаги (управляемый код)  
 Использовать службу образ, необходимо добавить в проект ссылки на некоторые или все из следующих сборок:  
  
-   **Microsoft.VisualStudio.ImageCatalog.dll**  
  
    -   Является обязательным, если используется встроенное изображение каталога KnownMonikers  
  
-   **Microsoft.VisualStudio.Imaging.dll**  
  
    -   Является обязательным, если используется **CrispImage** и **ImageThemingUtilities** в пользовательского Интерфейса WPF  
  
-   **Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll**  
  
    -   Является обязательным, если используется **ImageMoniker** и **ImageAttributes** типы  
  
    -   **EmbedInteropTypes** должно быть установлено в значение true  
  
-   **Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime**  
  
    -   Является обязательным, если используется **IVsImageService2** типа  
  
    -   **EmbedInteropTypes** должно быть установлено в значение true  
  
-   **Microsoft.VisualStudio.Utilities.dll**  
  
    -   Является обязательным, если используется **BrushToColorConverter** для ImageThemingUtilities.**ImageBackgroundColor** в пользовательского Интерфейса WPF  
  
-   **Microsoft.VisualStudio.Shell. \< VSVersion>.0**  
  
    -   Является обязательным, если используется **IVsUIObject** типа  
  
-   **Microsoft.VisualStudio.Shell.Interop.10.0.dll**  
  
    -   Требуется при использовании пользовательского интерфейса, связанные с WinForms помощников  
  
    -   **EmbedInteropTypes** должно быть установлено в значение true  
  
### <a name="first-steps-native"></a>Первые шаги (машинный код)  
 Использовать службу образ, необходимо включить некоторые или все из следующих заголовков в проект:  
  
-   **KnownImageIds.h**  
  
    -   Является обязательным, если используется каталога встроенное изображение **KnownMonikers**, но нельзя использовать **ImageMoniker** типа, например когда возвращение значения из **IVsHierarchy GetGuidProperty** или **GetProperty** вызовов.  
  
-   **KnownMonikers.h**  
  
    -   Является обязательным, если используется каталога встроенное изображение **KnownMonikers**.  
  
-   **ImageParameters140.h**  
  
    -   Является обязательным, если используется **ImageMoniker** и **ImageAttributes** типов.  
  
-   **VSShell140.h**  
  
    -   Является обязательным, если используется **IVsImageService2** типа.  
  
-   **ImageThemingUtilities.h**  
  
    -   Требуется, если не удается обрабатывать темы службой изображения.  
  
    -   Не используйте этот заголовок, если служба образов может обработать ваш образ темы.  
  
-   **VSUIDPIHelper.h**  
  
    -   Обязательным, если используется помощников DPI для получения текущего точек на ДЮЙМ.  
  
## <a name="how-do-i-write-new-wpf-ui"></a>Как написать новый пользовательский Интерфейс WPF?  
  
1.  Начните с добавления ссылки на сборки, необходимые в приведенном выше начальные действия раздела в проект. Не нужно добавить их все, поэтому добавьте ссылки, что нужно. (Примечание: Если вы используете или иметь доступ к **Цвета** вместо **кисти**, вы можете перейти ссылку на **служебных программ**, поскольку не требуется преобразователь.)  
  
2.  Выберите нужный образ и получить его моникера. Используйте **KnownMoniker**, или использовать собственную при наличии собственных пользовательских образов и специальные имена.  
  
3.  Добавить **CrispImages** в коде XAML. (См. ниже примере).  
  
4.  Задайте **ImageThemingUtilities.ImageBackgroundColor** свойство в иерархии пользовательского Интерфейса. (Это должно быть значение в месте, где цвет фона известен, не обязательно в **CrispImage**.) (См. ниже примере).  
  
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
  
 **Как обновить существующий пользовательский Интерфейс WPF?**  
  
 Обновление существующего пользовательского интерфейса WPF является сравнительно простой процесс, который состоит из трех основных этапов:  
  
1.  Заменить все \< изображение> элементов пользовательского Интерфейса с \< CrispImage> элементы  
  
2.  Изменить все атрибуты исходного моникера атрибутов  
  
    -   Если изображение не меняется, и вы используете **KnownMonikers**, статически привязки, свойства **KnownMoniker**. (См. приведенный выше пример).  
  
    -   Если изображение не меняется, и вы используете пользовательский образ, статически связать с собственные моникера.  
  
    -   Если изображение можно изменить, привязать атрибут моникер код свойству, которое уведомляет об изменениях свойств.  
  
3.  Где-то в иерархии пользовательского Интерфейса, задайте **ImageThemingUtilities.ImageBackgroundColor** Чтобы убедиться, что инверсия цветов работает правильно.  
  
    -   Это может потребовать использования **BrushToColorConverter** класса. (См. приведенный выше пример).  
  
## <a name="how-do-i-update-win32-ui"></a>Как обновить пользовательский Интерфейс Win32?  
 Добавьте следующий код, везде, где соответствующие замените необработанные загрузки изображения. Переключение значений для возврата HBITMAP и HICONs и HIMAGELIST при необходимости.  
  
 **Получение службы изображения**  
  
```cpp  
CComPtr<IVsImageService2> spImgSvc;  
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);  
```  
  
 **Запрос изображения**  
  
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
 Добавьте следующий код, везде, где соответствующие замените необработанные загрузки изображения. Переключение значений для возврата точечные рисунки и значки, при необходимости.  
  
 **Информативные, с помощью инструкции**  
  
```c#  
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;  
```  
  
 **Получение службы изображения**  
  
```c#  
// This or your preferred way of querying for Visual Studio services  
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));  
  
```  
  
 **Запрос изображения**  
  
```c#  
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
  
## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Использование моникеров изображение в новое окно инструмента  
 Шаблон проекта VSIX пакет был обновлен для Visual Studio 2015. Чтобы создать новое окно инструмента, правой кнопкой мыши проект VSIX и выберите «Добавить новый элемент...» (Ctrl + Shift + A). В узле расширения языка проекта выберите «Собственное окно средства», присвойте имя окна средства и нажмите кнопку «Добавить».  
  
 Это ключевых местах использовать специальные имена в окне инструментов. Следуйте инструкциям для каждого.  
  
1.  Вкладка окна инструментов при небольших вкладки достаточно (также используется в переключателе окна Ctrl + Tab).  
  
     Добавьте следующую строку в конструктор для класса, производного от **ToolWindowPane** типа:  
  
    ```c#  
    // Replace this KnownMoniker with your desired ImageMoniker  
    this.BitmapImageMoniker = KnownMonikers.Blank;  
    ```  
  
2.  Команду, чтобы открыть окно инструментов.  
  
     В файле .vsct для пакета измените окно инструментов кнопки:  
  
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
  
 Обновление существующему окну средство, чтобы использовать моникеры изображение аналогичны шагам, необходимым для создания нового окна инструмента.  
  
 Это ключевых местах использовать специальные имена в окне инструментов. Следуйте инструкциям для каждого.  
  
1.  Вкладка окна инструментов при небольших вкладки достаточно (также используется в переключателе окна Ctrl + Tab).  
  
    1.  Удалите следующие строки (если они существуют) в конструктор для класса, производного от **ToolWindowPane** типа:  
  
        ```c#  
        this.BitmapResourceID = <Value>;  
        this.BitmapIndex = <Value>;  
        ```  
  
    2.  См. шаг #1 из «Практические советы моникеров используйте изображение в новое окно инструмента?» выше.  
  
2.  Команду, чтобы открыть окно инструментов.  
  
    -   См. шаг #2 «Практические советы моникеров используйте изображение в новое окно инструмента?» выше.  
  
## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Использование моникеров изображения в файле .vsct  
 Добавьте в файл .vsct, обозначенный Закомментированные строки ниже:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <!--  Include the definitions for images included in the VS image catalog -->  
  <Include href="KnownImageIds.vsct"/>  
  <Commands package="guidMyPackage">  
    <Buttons>  
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">  
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.  
             In this case, we’re using the Guid for the VS image catalog.  
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
  
 **Что делать, если мой файл .vsct также необходимо прочитать старых версий Visual Studio?**  
  
 Более ранние версии Visual Studio не распознают **IconIsMoniker** команды флаг. Можно использовать образы из служба образов в версиях Visual Studio, которые его поддерживают, но по-прежнему использовать старый стиль изображения в старых версиях Visual Studio. Для этого бы оставить файл .vsct без изменений (и поэтому совместимы с более ранними версиями Visual Studio) и создать файл CSV (значения, разделенные запятыми), сопоставляющий из пары GUID-идентификатор, определенный в файле .vsct \< точечные рисунки> элемента изображения моникера или идентификатора GUID пары.  
  
 Имеет формат CSV-файла сопоставления:  
  
```  
Icon guid, Icon id, Moniker guid, Moniker id  
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100  
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200  
```  
  
 CSV-файл развертывается в составе пакета и его расположение задается путем **IconMappingFilename** свойство **ProvideMenuResource** атрибут пакета:  
  
```c#  
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]  
```  
  
  **IconMappingFilename** относительный путь неявно корнем $PackageFolder$ (как в приведенном выше примере) или абсолютный путь явно корнем определяется переменной среды, такие как каталог @"%UserProfile%\dir1\dir2\MyMappingFile.csv".  
  
## <a name="how-do-i-port-a-project-system"></a>Как перенести система проектов?  
 **Как предоставить ImageMonikers для проекта**  
  
1.  Реализуйте **VSHPROPID_SupportsIconMonikers** в проекте **IVsHierarchy**, и возвращают значение true.  
  
2.  Реализовать **VSHPROPID_IconMonikerImageList** (если используется исходный проект **VSHPROPID_IconImgList**) или **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (если используется исходный проект **VSHPROPID_IconHandle** и **VSHPROPID_OpenFolderIconHandle**).  
  
3.  Измените реализацию исходного VSHPROPIDs для значков для создания «устаревших» версий значки, если запрошены точек расширения. **IVsImageService2** предоставляет функциональные возможности, необходимые для получения этих значков  
  
 **Дополнительные требования для VB / C# разновидности**  
  
 Реализовать только **VSHPROPID_SupportsIconMonikers** при обнаружении проекта **внешней flavor**. В противном случае — фактическое внешняя версия может не поддерживать моникеров изображения на самом деле и вашей базовой версии может эффективно «скрыть» настроенных образов.  
  
 **Использование моникеров изображения в CPS**  
  
 Задание пользовательских образов в CPS (проекта система) можно сделать вручную или с помощью шаблона элемента, который поставляется с пакетом SDK для расширения системы проекта.  
  
 **Используя пакет SDK ДЛЯ расширения системы проекта**  
  
 Следуйте инструкциям в [предоставляют собственные значки для типа элемент типа проекта](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) для настройки CPS изображений. Дополнительные сведения о CPS можно найти в [документации проекта расширения системы Visual Studio](https://github.com/Microsoft/VSProjectSystem)  
  
 **Можно вручную настроить ImageMonikers**  
  
1.  Реализация и экспортировать **IProjectTreeModifier** интерфейса в систему проектов.  
  
2.  Определить, какие **KnownMoniker** или вы хотите использовать специальное имя пользовательского образа.  
  
3.  В **ApplyModifications** метод, выполните следующие действия где-то в методе перед возвратом нового дерева, аналогично ниже примере:  
  
    ```c#  
    // Replace this KnownMoniker with your desired ImageMoniker  
    tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());  
    ```  
  
4.  При создании нового дерева, можно задать пользовательские изображения, передавая нужное моникеры в метод NewTree, аналогично ниже примере:  
  
    ```c#  
    // Replace this KnownMoniker with your desired ImageMoniker  
    ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();  
    ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();  
  
    return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,  
                                                 /*filePath*/<value>,  
                                                 /*browseObjectProperties*/<value>,  
                                                 icon,  
                                                 expandedIcon);  
    ```  
  
## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Как преобразование панелью реального изображения для полосковых образов на основе моникера?  
 **Требуется ли поддержка HIMAGELISTs**  
  
 Если группа уже существующих изображений для кода, необходимо обновить для использования службы изображения, но ограничиваются программные интерфейсы, требующие пересылку списков изображений, можно получить преимущества службы изображения. Чтобы создать образ на основе моникера полоса, выполните следующие шаги для создания манифеста из существующих моникеры.  
  
1.  Запустите **ManifestFromResources** средство, передавая ему полосу изображения. Это создаст манифеста полосе.  
  
    -   Рекомендуется: укажите имя не по умолчанию для манифеста в соответствии с его использования.  
  
2.  Если вы используете только **KnownMonikers**, затем выполните следующие действия:  
  
    -   Замените \< изображения> раздел манифеста с \< изображения или>.  
  
    -   Удалите все идентификаторы subimage (все символы с \< имя imagestrip>_ ##).  
  
    -   Рекомендуется: переименуйте символ AssetsGuid и изображение полосковой символов в соответствии с его использования.  
  
    -   Замените каждый **ContainedImage**GUID с $(ImageCatalogGuid), замените каждый **ContainedImage**ИДЕНТИФИКАТОР с $(\<moniker>) и добавьте атрибут внешних = «true» для каждого **ContainedImage**  
  
        -   \< моникер> должно быть заменено **KnownMoniker** соответствующий образ, но с «KnownMonikers». удалены из имени.  
  
    -   Добавьте < Импорт Manifest="$(ManifestFolder)\\< установите относительный путь к папке для\>\Microsoft.VisualStudio.ImageCatalog.imagemanifest» и\> в верхнюю часть \< символы> раздел.  
  
        -   Относительный путь определяется расположение развертывания, определенные в программе установки, создания манифеста.  
  
3.  Запустите **ManifestToCode** средства для создания оболочек, таким образом, существующий код имеет специальное имя, его можно использовать для запроса к службе изображение полосу изображения.  
  
    -   Рекомендуется: задайте нестандартные имена оболочки и пространства имен в соответствии с их использования.  
  
4.  Выполните все добавляет, разработки и развертывания и установки и другие изменения кода для работы со службой образов в и новые файлы.  
  
 Пример манифеста, включая внутренние и внешние изображения, чтобы увидеть, как она должна выглядеть:  
  
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
  
1.  Определить набор **KnownMonikers** соответствует изображений в ваш полосу изображения, или создать собственные специальные имена для изображений в вашей полосу изображения.  
  
2.  Обновите любые сопоставления, используемые для получения изображения по индексу, необходимые в полосе образа, вместо этого использовать специальные имена.  
  
3.  Обновите код для использования службы изображения для запроса моникеров через обновленного сопоставления. (Это может означать обновление для **CrispImages** для управляемого кода, или запрашивать HBITMAP или HICONs из образа службы и передача их вокруг машинного кода.)  
  
## <a name="testing-your-images"></a>Тестирование изображения  
 Средство просмотра изображений библиотеки можно использовать для тестирования манифесты изображение, чтобы убедиться в том, что все, что создан правильно. Можно найти средство в [пакет SDK ДЛЯ Visual Studio 2015](http://msdn.microsoft.com/library/bb166441.aspx). Можно найти документацию по этой и другими инструментами [здесь](http://aka.ms/VSImageThemeTools).  
  
## <a name="additional-resources"></a>Дополнительные ресурсы  
  
### <a name="samples"></a>Примеры  
 Некоторые примеры Visual Studio на GitHub были обновлены для демонстрации способов используют службу образов в составе разных точках расширяемости Visual Studio.  
  
 Проверьте [http://github.com/Microsoft/VSSDK-Extensibility-Samples](http://github.com/Microsoft/VSSDK-Extensibility-Samples) последние примеры.  
  
### <a name="tooling"></a>Инструментарий  
 Набор средств поддержки службы образов в был создан для помощи в создании или обновлении пользовательский Интерфейс, который работает со службой образов. Дополнительные сведения о каждом инструменте просмотрите документацию, поставляемую вместе со средствами. Средства включены в состав [пакет SDK ДЛЯ Visual Studio 2015.](http://msdn.microsoft.com/library/bb166441.aspx)  
  
 **ManifestFromResources**  
  
 Манифест из ресурсов средства принимает список ресурсов изображений (PNG или XAML) и создает файл манифеста изображения для использования со службой образов в этих образов.  
  
 **ManifestToCode**  
  
 Манифест, чтобы средство кода принимает файл манифеста изображения и создает файл программы-оболочки для ссылки на значения манифеста в коде (C++, C# или VB) или vsct-файлы.  
  
 **ImageLibraryViewer**  
  
 Средство просмотра изображений библиотеки можно загрузить образ манифесты и позволяет пользователю работать с ними так же, как Visual Studio и убедитесь, что манифест создан правильно. Пользователь может изменить фон, размеры, параметр DPI, высокая контрастность и другие параметры. Также отображает сведения о загрузки для поиска ошибок в манифестах и отображает сведения об источнике для каждого изображения в манифесте.  
  
## <a name="faq"></a>часто задаваемые вопросы  
  
-   Существуют ли все зависимости, которые необходимо включить при загрузке \< Include="Microsoft.VisualStudio.* ссылки. Interop.14.0.DesignTime» и>?  
  
    -   Задать EmbedInteropTypes = «true» на все библиотеки DLL взаимодействия.  
  
-   Развертывание образа манифеста с расширением my  
  
    -   Добавьте файл .imagemanifest в проект.  
  
    -   Задайте для параметра «Включить в VSIX» значение True.  
  
-   Обновлении системы проекта CPS Что случилось с **ImageName** и **StockIconService**?  
  
    -   o, они были удалены в ходе CPS был обновлен для использования специальных имен. Вам больше не нужно вызывать **StockIconService**, просто передайте нужный **KnownMoniker** метода или свойства с помощью **ToProjectSystemType()** метод расширения в служебных программах CPS. Можно найти сопоставление **ImageName** для **KnownMonikers** ниже:  
  
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
  
    -   Обновлении моего поставщика списка завершения. Что **KnownMonikers** соответствуют старым **StandardGlyphGroup** и **StandardGlyph** значения?  
  
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
        |GlyphAssembly||Ссылки|  
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
        |GlyphJSharpProject||Коллекции документов|  
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