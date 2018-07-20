---
title: Адресация DPI Issues2 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 97012b0d8b4214cdeafcaf12403948997436a212
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154334"
---
# <a name="address-dpi-issues"></a>Разрешение проблем
Все большее число устройств входят в состав экранов «высокого разрешения». Эти экраны обычно имеют более чем 200 пикселей на дюйм (ppi). Для работы с приложением на этих компьютерах потребуется содержимого масштаба для удовлетворения потребностей Просмотр содержимого на расстоянии обычный режим просмотра для устройства. Начиная с 2014 г. основного целевого объекта, для дисплеев с высокой плотностью мобильных вычислительных устройств (планшеты, ноутбуки лотке и телефоны).  
  
 Windows 8.1 и более поздних версий содержит несколько функций, чтобы включить эти компьютеры для работы с отображает и средах, где компьютер подключен к обоим с высокой плотностью и отображает плотность standard в то же время.  
  
-   Windows позволяет вам масштабировать содержимое на устройство с помощью «сделать текст и другие элементы больше или меньше» установка (доступно начиная с Windows XP).  
  
-   Windows 8.1 и более поздних версий автоматически выполнит масштабирование содержимого для большинства приложений для согласования, при перемещении между отображает различные плотности пикселей. При основное устройство отображения с высокой плотностью (масштабирование 200%) и дополнительный дисплей стандартный плотность (100%), Windows будет автоматически уменьшать содержимое окна приложения на дополнительный дисплей (1 пиксель, отображаемый для каждые 4 точкам, преобразовываемый для просмотра приложение).  
  
-   Windows по умолчанию справа масштабирование от плотности пикселей и просмотр расстояние для устройства отображения (Windows 7 и более поздних версий, можно настроить OEM).  
  
-   Windows может автоматически масштабировать содержимого вверх на 250% на новых устройствах, которые превышают 280 пикселей на дюйм (начиная с Windows 8.1 S14).  
  
 Windows имеет возможность работы с масштабированием пользовательского интерфейса воспользоваться преимуществами повышенной пикселей счетчиков. Приложения принимает решение в этой системе, объявив себя «system DPI, получить». Приложения, которые этого не сделать увеличивать с помощью системы. Это может привести к взаимодействия с пользователем «Нечеткое» где всего приложения, равномерно растягивается пикселей. Пример:  
  
 ![Точек на ДЮЙМ выдает нечеткого](../extensibility/media/dpi-issues-fuzzy.png "DPI выдает нечетких соответствий")  
  
 Visual Studio позволяет, поддерживающего масштабирование DPI и таким образом не «виртуализируется.»  
  
 Windows (и Visual Studio) используют несколько технологий пользовательского интерфейса, которые имеют различные способы работы с системой коэффициенты масштабирования. Пример:  
  
-   WPF измеряет элементов управления в аппаратно независимым способом (единицы, не в пикселах). Пользовательский Интерфейс WPF автоматически масштабируется для получения текущего значения DPI.  
  
-   Все размеры текста независимо от платформы пользовательского интерфейса выражаются в точках и таким образом, обрабатываются системой как независимый от точек на ДЮЙМ. Текст в WPF, WinForms и Win32 уже увеличивать масштаб правильно при выводе на устройство отображения.  
  
-   Win32/WinForms диалоговых окон и окон иметь средство включения макет, который изменяет размер с текстом (например, с помощью сетки, flow и панели макета таблицы). Это позволяет избежать расположений жестко пикселей, которые не масштабируются при увеличиваются размеры шрифтов.  
  
-   Значки, предоставляемые системой или ресурсы, на основе метрик системы (например, SM_CXICON и SM_CXSMICON) уже масштабируются.  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Более старые Win32 (GDI, GDI +) и пользовательского интерфейса на базе WinForms  
 Хотя WPF высокой поддерживает определение DPI, большая часть нашего кода на базе Win32/GDI не было записано первоначально с поддержки определения DPI в виду. Windows предоставляет интерфейсы API, масштабирование DPI. Исправления для проблемы Win32 следует использовать их постоянно по продукту. Visual Studio предоставляет вспомогательный объект библиотеки классов, чтобы избежать дублирования функциональности и обеспечение согласованности с продуктом.  
  
## <a name="high-resolution-images"></a>Изображения с высоким разрешением  
 Этот раздел предназначен главным образом для разработчиков, расширение Visual Studio 2013. Для Visual Studio 2015 используйте службу образов, который встроен в Visual Studio. Также может оказаться, что необходимо для поддержки и целевого многих версий Visual Studio, и таким образом с помощью службы образов в 2015 не подходит, так как он не существует в предыдущих версиях. В этом разделе будет также автоматически.  
  
## <a name="scaling-up-images-that-are-too-small"></a>Масштабирование изображений, которые слишком малы  
 Образы, которые слишком малы можно масштабировать в сторону увеличения и отображается GDI и WPF, используя некоторые распространенные методы. Вспомогательные классы управляемых точек на ДЮЙМ, доступны для внутренних и внешних интеграторов Visual Studio по адресу масштабированию значки, растровые изображения, imagestrips и imagelists. На базе Win32 машинном языке C / C ++ вспомогательные функции доступны для масштабирования HICON, HBITMAP, HIMAGELIST и VsUI::GdiplusImage. Только масштабирование растрового изображения обычно требует изменения одной строки после ссылки на вспомогательную библиотеку. Пример:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Масштабирование изображений зависит от ли список imagelist завершена во время загрузки или добавляется во время выполнения. Если полные во время загрузки, вызовите `LogicalToDeviceUnits()` с imagelist, как вы бы растрового изображения. Когда код должен загрузить отдельные точечный рисунок перед построением imagelist, убедитесь, что масштабировать размер образа imagelist:  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 В машинном коде можно масштабировать размеры при создании imagelist следующим образом:  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Функции в библиотеке разрешается указывать алгоритм изменения размера. Когда масштабирования изображения должно быть помещено в imagelists, не забудьте указать цвет фона, используемый для прозрачности или используется NearestNeighbor масштабирование (в результате чего искажения в в 125% и 150 ° %).  
  
 Обратитесь к <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> документации на сайте MSDN.  
  
 Ниже приведены примеры способ масштабирования изображения соответствующих точек на дюйм коэффициенты масштабирования. Образы зеленым цветом обозначения наши рекомендации по состоянию на Visual Studio 2013 (100 – 200% масштабирование):  
  
 ![Масштабирование в проблемах с DPI](../extensibility/media/dpi-issues-scaling.png "масштабирование в проблемах с DPI")  
  
## <a name="layout-issues"></a>Проблемы с макетом  
 Распространенные проблемы с макетом можно избежать, главным образом сохраняя точки в пользовательском Интерфейсе масштабируется и относительно друг друга, а не с помощью абсолютного расположения (в частности, в единицах пикселей). Пример:  
  
-   Макет/текста необходимо настроить учетную запись для масштабируемых образов.  
  
-   Столбцы в таблицах должны иметь ширина которых скорректирована для масштабируемых текста.  
  
-   Жестко размеры или пространство между элементами также потребуется увеличить масштаб. Размеры, основанные только на размеры текста обычно работают нормально, поскольку шрифты автоматически масштабируются.  
  
 Вспомогательные функции доступны в <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> класс для масштабирования по осям X и Y:  
  
-   LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (разрешить функции масштабирования в X и оси Y)  
  
-   int пространства = DpiHelper.LogicalToDeviceUnitsX (10);  
  
-   int height = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);  
  
 Существуют перегрузки LogicalToDeviceUnits для масштабирования объекты, такие как Rect, точки и размер.  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>С помощью библиотеки DPIHelper/класса масштабирование изображений и макет  
 Вспомогательную библиотеку Visual Studio DPI доступен в формах машинного и управляемого кода и может использоваться другими приложениями за пределами оболочки Visual Studio.  
  
 Чтобы использовать библиотеку, перейдите к статье [примеры расширяемости Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) и клонируйте пример высокой DPI_Images_Icons.  
  
 В файлах исходного кода включают *VsUIDpiHelper.h* вызовов статические функции `VsUI::DpiHelper` класса:  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  Не используйте вспомогательные функции в статических переменных уровня класса или модуля. Библиотека также использует статические элементы для синхронизации потоков, и вы можете столкнуться проблемы порядок инициализации. Преобразование этих статических элементов в нестатических-переменные члены или помещать их в функцию (поэтому они конструировать при первом доступе).  
  
 Для доступа к DPI вспомогательные функции из управляемого кода, который будет выполняться в среде Visual Studio:  
  
-   Потребляющий проект должен ссылаться на последнюю версию оболочки MPF. Пример:  
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Убедитесь в проекте имеются ссылки на **System.Windows.Forms**, **PresentationCore**, и **PresentationUI**.  
  
-   В коде используйте **Microsoft.VisualStudio.PlatformUI** пространства имен и вызова статических функций класса DpiHelper. Для поддерживаемых типов (точек, размеры, прямоугольники и т. д.) существует предоставляются функции расширения, которые возвращают новые масштабировать объекты. Пример:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Работа с WPF разброс изображение в пользовательском Интерфейсе масштабируемым  
 В WPF растровые изображения изменяется автоматически платформой WPF для текущего уровня масштаба DPI, с помощью алгоритма бикубическую высокого качества (по умолчанию), который хорошо подходит для изображений или крупных снимки экрана, но не подходит для значки элементов меню, так как она порождает предполагаемых разброс .  
  
 Рекомендуемые действия.  
  
-   Для логотипа образ и баннеров графический объект, значение по умолчанию <xref:System.Windows.Media.BitmapScalingMode> изменение размера режим может использоваться.  
  
-   Для элементов меню и образы иллюстрациях <xref:System.Windows.Media.BitmapScalingMode> следует использовать, если оно не вызывает другие артефакты искажение во избежание разброс (в 200% и 300%).  
  
-   Для масштабирования больших уровней не кратна 100% (например, 250% или 350%), масштабирование изображений иллюстрациях с бикубическую приводит нечетких соответствий, размытый вид пользовательского интерфейса. Наилучшего результата получается путем масштабирования изображения с NearestNeighbor до наибольшего кратного 100% (например, 200 или 300%) и масштабирование с помощью бикубическую оттуда. См. в разделе особый случай: prescaling изображений WPF для DPI в больших уровни Дополнительные сведения.  
  
 Класс DpiHelper в пространстве имен Microsoft.VisualStudio.PlatformUI предоставляет членом <xref:System.Windows.Media.BitmapScalingMode> , можно использовать для привязки. Это позволит оболочке Visual Studio для управления растровое изображение, режим масштабирования с продуктом равномерно, в зависимости от коэффициента масштабирования точек на ДЮЙМ.  
  
 Чтобы использовать его в XAML, добавьте следующую команду:  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Оболочка Visual Studio уже устанавливает это свойство для окон верхнего уровня и диалоговые окна. Пользовательский Интерфейс на основе WPF в Visual Studio уже унаследует его. Если параметр не распространяется на определенной части пользовательского интерфейса, его можно установить в корневом элементе пользовательского интерфейса XAML и WPF. Мест, где это происходит, включают всплывающие окна, на элементы с родительскими элементами Win32, и обрабатывать конструктора окон, которые запускаются из, например Blend.  
  
 Пользовательский Интерфейс можно масштабировать независимо от уровня масштабирования DPI набор системы, например текстового редактора Visual Studio и конструкторах на основе WPF (WPF для рабочей среды и Windows Store). В этих случаях DpiHelper.BitmapScalingMode использовать нельзя. Чтобы устранить эту проблему в редакторе, группа разработчиков СРЕДЫ, создать пользовательское свойство под названием RenderOptions.BitmapScalingMode. Установите это значение свойства HighQuality или NearestNeighbor в зависимости от объединенный масштаба системы и пользовательского интерфейса.  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Особый случай: prescaling изображений WPF для больших уровнями DPI  
 Для очень большого масштаба, которые не кратна 100% (например, 250% 350% и т. д.) масштабирование изображений иллюстрациях с результатами бикубическую в пользовательском Интерфейсе нечетких соответствий, цвета. Эффекта этих образов вместе с четким текстом похожа почти иллюзия оптическое. То изображения появляются быть ближе для глаза и нерезко по отношению к тексту. Результат масштабирования при таком размере увеличенной можно повысить путем масштабирования изображения с NearestNeighbor до наибольшего кратного 100% (например, 200 или 300%) и масштабирование с помощью бикубическую остаток (дополнительные 50%).  
  
 Ниже приведен пример различия в результатах, где первое изображение масштабируется алгоритму улучшенное масштабирование двойной 100% "->" 200% -> 250%, а второй только с бикубическую 100% -> 250%.  
  
 ![Точек на ДЮЙМ выдает Double пример масштабирования](../extensibility/media/dpi-issues-double-scaling-example.png "DPI выдает Double пример масштабирования")  
  
 Чтобы включить пользовательский Интерфейс будет использоваться этот масштабирование двойной, разметка XAML для отображения каждого элемента изображения, должны быть изменены. Следующие примеры демонстрируют, как использовать масштабирование двойной в WPF в Visual Studio, используя библиотеку DpiHelper и Shell.12/14.  
  
 Шаг 1: Prescale изображение, 200%, 300% и так далее с помощью NearestNeighbor.  
  
 Prescale изображения с помощью преобразователя, применяется для привязки, или с использованием расширения разметки XAML. Пример:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Если образ также должен быть оформлены тематически (большинство, если не все, следует), разметки можно использовать различные преобразователь, который сначала выполняет темы изображения, а затем предварительно масштабирование. Можно использовать разметку <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> или <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>в зависимости от требуемое преобразование выходных данных.  
  
```xaml  
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />  
  
<Image Width="16" Height="16">  
  <Image.Source>  
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">  
      <Binding Path="Icon" />  
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"    
               RelativeSource="{RelativeSource Self}" />  
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />  
    </MultiBinding>  
  </Image.Source>  
</Image>  
```  
  
 Шаг 2: Убедитесь, что конечный размер подходит для текущей точек на ДЮЙМ.  
  
 Поскольку WPF масштабирования пользовательского интерфейса для текущего DPI, используя свойство BitmapScalingMode UIElement, следует элемент Image, с помощью prescaled образа, как его источник будет выглядеть два или три раза больше, чем его. Вот несколько способов для борьбы с такого эффекта:  
  
-   Если вы знаете измерения исходного изображения в масштабе 100%, можно указать точный размер элемента управления Image. Эти размеры отразят применяется размер пользовательского интерфейса перед масштабированием.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Если размер исходного изображения не известен, преобразованием LayoutTransform можно масштабировать итогового объекта образа. Пример:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>Включение поддержки HDPI для WebOC  
 По умолчанию элементы управления WebOC (например, элемент управления WebBrowser в WPF или интерфейса IWebBrowser2) не включайте обнаружение HDPI и поддержки. Результатом будет внедренный элемент управления с Показывать содержимое, которое слишком мало, на экране с высоким разрешением. Ниже описано, как для поддержки высокого DPI в экземпляре WebOC конкретных web.  
  
 Реализация интерфейса IDocHostUIHandler (см. в статье MSDN на [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) интерфейса):  
  
```idl  
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]  
public interface IDocHostUIHandler  
{  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowContextMenu(  
        [In, MarshalAs(UnmanagedType.U4)] int dwID,  
        [In] POINT pt,  
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,  
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowUI(  
        [In, MarshalAs(UnmanagedType.I4)] int dwID,  
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,  
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,  
        [In, MarshalAs(UnmanagedType.Interface)] object frame,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int HideUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int UpdateUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ResizeBorder(  
        [In] COMRECT rect,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc,  
        bool fFrameWindow);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateAccelerator(  
        [In] ref MSG msg,  
        [In] ref Guid group,  
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetOptionKeyPath(  
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,  
        [In, MarshalAs(UnmanagedType.U4)] int dw);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetDropTarget(  
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,  
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateUrl(  
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,  
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,  
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int FilterDataObject(  
        IDataObject pDO,  
        out IDataObject ppDORet);  
    }   
```  
  
 При необходимости реализовать интерфейс ICustomDoc (см. в статье MSDN на [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) интерфейса):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Свяжите класс, реализующий IDocHostUIHandler с документом WebOC. Если приведенный выше интерфейс ICustomDoc реализован, как только свойство WebOC документа является допустимым, выполнить его приведение к ICustomDoc затем вызовите метод SetUIHandler, передав класс, реализующий IDocHostUIHandler.  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 Если вы не реализует интерфейс ICustomDoc, то как только свойство документа WebOC допустим, вам потребуется выполнить его приведение к IOleObject и вызовите метод `SetClientSite` , передавая в класс, реализующий IDocHostUIHandler. Задан флаг DOCHOSTUIFLAG_DPI_AWARE DOCHOSTUIINFO, передаваемый `GetHostInfo` вызов метода:  
  
```csharp  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 Это должна быть все, что вам нужно получить WebOC управления должно поддерживать HPDI.  
  
## <a name="tips"></a>Советы  
  
1.  При изменении свойства документа в элементе управления WebOC, может потребоваться повторное связывание документа с помощью класса IDocHostUIHandler.  
  
2.  Если оно не работает, имеется известная проблема, не получает изменения DPI флаг WebOC. Самый надежный способ исправления этого является переключать визуальное масштабирование WebOC, два вызова значение с двумя разными значениями для масштабирования в процентах. Кроме того при необходимости этот обходной путь, возможно, необходимо выполнить его при каждом вызове Навигатор.  
  
    ```csharp  
    // browser2 is a SHDocVw.IWebBrowser2 in this case  
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values  
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;  
    if (cmdTarget != null)  
    {  
        object commandInput = zoomPercent;  
        cmdTarget.Exec(IntPtr.Zero,  
                       OLECMDID_OPTICAL_ZOOM,  
                       OLECMDEXECOPT_DONTPROMPTUSER,  
                       ref commandInput,  
                       ref commandOutput);  
    }  
    ```