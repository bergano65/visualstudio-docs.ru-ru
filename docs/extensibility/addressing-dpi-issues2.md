---
title: "Адресация Issues2 точек на ДЮЙМ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Разрешение проблем
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Все большее число устройств поставляются экранов «высокого разрешения». Эти окна обычно имеют более 200 точек на дюйм \(ppi\). Работе с приложением на этих компьютерах потребует содержимого в масштабировании вверх в соответствии с потребностями просмотра содержимого на расстоянии обычный для устройства. Начиная с 2014 основная цель с высокой плотностью отображает мобильных вычислительных устройств \(планшетных ПК, ноутбуки лотке и телефоны\).  
  
 Windows 8.1 и более поздних версий содержит несколько функций, чтобы включить эти машины для работы с отображаются и в средах, где машина присоединена к обоим высокой плотности и отображает плотность standard в то же время.  
  
-   Windows позволяет вам масштабировать содержимое к устройству с помощью «сделать текст и другие элементы больше или меньше» \(доступным, начиная с Windows XP\).  
  
-   Автоматически масштабирует содержимого для большинства приложений будут согласованы, при перемещении между отображением разные плотности пикселей Windows 8.1 и более поздней версии. Когда основной дисплей является высокая плотность \(200% масштабирование\) и дополнительный дисплей — Стандартная плотность \(100%\), Windows будет автоматически снижайте содержимое окна приложения на дополнительный дисплей \(отображается каждые 4 точек, к просмотру приложением 1 пиксель\).  
  
-   Windows по умолчанию право масштабирования плотности пикселей и просмотр расстояния для отображения \(Windows 7 и более поздних версий, можно настроить OEM\).  
  
-   Windows позволяет автоматически масштабировать содержимого вверх на 250% на новых устройствах, которые превышают 280 ppi \(начиная с Windows 8.1 S14\).  
  
 Windows имеет возможность работы с масштабированием пользовательского интерфейса воспользоваться преимуществами повышенной пикселей счетчиков. Приложение позволяет использовать эту систему, объявив себя «system ДЮЙМ». Приложения, которые этого не сделать масштабируемых системой. Это может привести к «Нечеткий» пользователя, где равномерно увеличить пикселей всего приложения. Пример:  
  
 ![Проблемы с четкостью DPI](../extensibility/media/dpi-issues-fuzzy.png "DPI Issues Fuzzy")  
  
 Visual Studio позволяет использовать поддерживающее масштабирование DPI и таким образом не «виртуализован.»  
  
 Windows \(Visual Studio\) использовать несколько технологий пользовательского интерфейса, которые имеют разные способы работы с системой коэффициенты масштабирования. Пример:  
  
-   WPF измеряет элементов управления в виде аппаратно независимые \(единицы, не в пикселах\). Пользовательский Интерфейс WPF автоматически масштабируется для текущего точек на ДЮЙМ.  
  
-   Все размеры текста независимо от платформы пользовательского интерфейса выражаются в пунктах и таким образом, обрабатываются системой как независимые точек на ДЮЙМ. Текст в Win32, WPF и WinForms уже масштабирование правильно при выводе на устройство отображения.  
  
-   Win32\/WinForms диалоговые окна и окна обладать средствами для включения макета, изменять размеры текста, например, через сетку, поток и панели макета таблицы. Это позволяет избежать расположения жестко пикселей, которые не масштабируются при увеличении размеров шрифта.  
  
-   Значки, предоставленную системой или ресурсам на основании метрик системы \(например, SM\_CXICON и SM\_CXSMICON\) уже масштабировании вверх.  
  
## Более старые Win32 \(GDI, GDI \+\) и пользовательского интерфейса на базе WinForms  
 Хотя WPF высокой дюйм, большая часть нашего кода на базе Win32\/GDI не было записано изначально использованием DPI в виду. Windows предоставляет API\-интерфейсы масштабированием DPI. Исправления для проблем Win32 следует использовать их постоянно по продукту. Visual Studio предоставляет вспомогательный класс библиотеки классов, чтобы избежать дублирования функций и обеспечение согласованности по продукту.  
  
## Изображения с высоким разрешением  
 Этот раздел предназначен главным образом для разработчиков в расширение Visual Studio 2013. Для Visual Studio 2015 используют службу образов, который встроен в Visual Studio. Также может оказаться, что требуется для поддержки и целевого многих версий Visual Studio, и таким образом с помощью службы изображения в 2015 вариант невозможен, поскольку он не существует в предыдущих версиях. В этом разделе будет также автоматически.  
  
## Масштабирование изображений, которые слишком велики  
 «Масштабирования» и отображается GDI и WPF, используя некоторые распространенные методы образы, которые слишком малы. Управляемые DPI вспомогательные классы доступны для внутренних и внешних интеграторов Visual Studio по адресу масштабирование значки, растровые изображения, imagestrips и imagelists. На базе Win32 собственного C \/ C \+\+ вспомогательные методы, доступных для масштабирования HICON, HBITMAP, HIMAGELIST и VsUI::GdiplusImage. Только масштабирование растрового изображения обычно требует изменения одной строки после ссылки на вспомогательной библиотеке. Пример:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```c#  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Масштабирование изображений зависит ли imagelist во время загрузки или завершения добавляется во время выполнения. Если полный во время загрузки, вызовите LogicalToDeviceUnits\(\) с imagelist как растровое изображение. Когда код для загрузки отдельного растрового перед составление imagelist, убедитесь, что масштабировать размер изображения для изображений из списка:  
  
```c#  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 В машинном коде измерений можно масштабировать при создании imagelist следующим образом:  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Функции в библиотеке разрешает указание алгоритм изменения размера. Когда масштабирования изображения следует поместить в imagelists, не забудьте указать цвет фона, используемый для прозрачности или использовать NearestNeighbor масштабирование \(что приведет к искажений в 125% и 150%\).  
  
 Обратитесь к <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> в документации MSDN.  
  
 Ниже приведены примеры как образы масштабироваться соответствующих точек на дюйм коэффициенты масштабирования. Образы в зеленый цвет обозначения наши рекомендации по состоянию на Visual Studio 2013 \(100\-200% масштабирование\):  
  
 ![Масштабирование в проблемах с DPI](../extensibility/media/dpi-issues-scaling.png "DPI Issues Scaling")  
  
## Проблемы с макетом  
 Распространенные проблемы с макетом можно избежать, главным образом, не допуская точек в пользовательском Интерфейсе масштабируется и относительно друг друга, а не с помощью абсолютного расположения \(в частности, в единицах пикселей\). Пример:  
  
-   Макет и текста необходимо настроить учетную запись для масштабируемых изображения.  
  
-   Столбцы в таблицах должны иметь масштабируемых текста с учетом ширины.  
  
-   Жестко запрограммированные размеры или пробел между элементами также потребуется масштабировать в сторону. Размеры, основанные только на размеры текста обычно работают нормально, поскольку шрифты автоматически масштабируются.  
  
 Вспомогательные функции доступны в <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> класс, позволяющий масштабирования по оси X и Y:  
  
-   LogicalToDeviceUnitsX или LogicalToDeviceUnitsY \(разрешить функции масштабирования в X и оси Y\)  
  
-   int пространства \= DpiHelper.LogicalToDeviceUnitsX \(10\);  
  
-   int height \= VsUI::DpiHelper::LogicalToDeviceUnitsY\(5\);  
  
 Существуют перегрузки LogicalToDeviceUnits, чтобы обеспечить масштабирование объектов, например Rect, точки и размер.  
  
## С помощью библиотеки DPIHelper или класс масштабирование изображений и макета  
 Вспомогательной библиотеке Visual Studio DPI доступен в машинном и управляемом формах и может использоваться другими приложениями за пределами оболочки Visual Studio.  
  
 Чтобы использовать библиотеку, перейдите на [Примеры расширяемости Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) и клонирование высокой DPI\_Images\_Icons образца  
  
 В файлах исходного кода включают VsUIDpiHelper.h и вызова статических функций класса VsUI::DpiHelper:  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  Не используйте вспомогательных функций в статических переменных уровня класса или модуля. Библиотека также использует статических переменных для синхронизации потоков, и может выполняться в порядке инициализации неполадки. Преобразуйте эти помехи в нестатические переменные, либо поместить их в функции \(то есть они конструировать при первом доступе\).  
  
 Для доступа к DPI вспомогательных функций из управляемого кода, который будет выполняться в среде Visual Studio.  
  
-   Много проект должен ссылаться последнюю версию оболочки MPF. Пример:  
  
    ```c#  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Убедитесь в проекте есть ссылки на **System.Windows.Forms**, **PresentationCore**, и **PresentationUI**.  
  
-   В коде используйте **Microsoft.VisualStudio.PlatformUI** пространства имен и вызова статических функций класса DpiHelper. Для поддерживаемых типов \(точек, размеры, прямоугольников и т.д.\), предоставляемые масштабировать расширения функций, которые возвращают новые объекты. Пример:  
  
    ```c#  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## Работа с WPF разброс изображение в пользовательском Интерфейсе масштабируемым  
 В WPF растровые изображения изменяется автоматически в WPF для текущего уровня масштабирования точек на ДЮЙМ, с помощью алгоритма Бикубический высокого качества \(по умолчанию\), который хорошо подходит для изображений и больших снимки экрана, но не подходит для значки элементов меню, так как она порождает распознанный разброс.  
  
 Рекомендации:  
  
-   Для логотипа изображения и ленты графический объект, значение по умолчанию <xref:System.Windows.Media.BitmapScalingMode> можно использовать режим изменения размеров.  
  
-   Для элементов меню и образы иллюстрациях <xref:System.Windows.Media.BitmapScalingMode> следует использовать, если оно не вызывает другие артефакты искажения во избежание разброса \(в 200% и 300%\).  
  
-   •	Для масштабирования больших уровней не кратно 100% \(например, 250% или 350%\), масштабирование изображений иллюстрациях с Бикубический приводит нечеткого, размытый вид пользовательского интерфейса. Лучше результат получается путем масштабирования изображения с NearestNeighbor наибольшее нескольким 100% \(например, 200% или 300%\) и масштабирование с помощью Бикубический оттуда. В разделе особый случай: prescaling изображений WPF для больших DPI уровней для получения дополнительной информации.  
  
 Класс DpiHelper в пространстве имен Microsoft.VisualStudio.PlatformUI предоставляет член <xref:System.Windows.Media.BitmapScalingMode> может использоваться для привязки. Это позволит оболочке Visual Studio для управления точечного рисунка, в режиме масштабирования по продукту равномерным, в зависимости от коэффициента масштабирования точек на ДЮЙМ.  
  
 Чтобы использовать его в XAML, добавьте:  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Оболочка Visual Studio уже устанавливает это свойство для окон верхнего уровня и диалоговых окон. Пользовательский Интерфейс на основе WPF в Visual Studio уже будет наследовать его. Если параметр не распространяется на конкретной части пользовательского интерфейса, его можно задать в корневом элементе пользовательского интерфейса XAML и WPF. Мест, где это происходит включают всплывающих окон для элементов, имеющих родителей Win32, и обрабатывать конструктора окон, которые запускаются из, например Blend.  
  
 Пользовательский Интерфейс можно масштабировать независимо от уровня масштабирования DPI набор системы, например текстового редактора Visual Studio и конструкторах на основе WPF \(WPF для рабочей среды и магазина Windows\). В этих случаях DpiHelper.BitmapScalingMode использовать не следует. Чтобы устранить эту проблему в редакторе, группа разработчиков СРЕДЫ, создать пользовательское свойство под названием RenderOptions.BitmapScalingMode. Значение этого свойства HighQuality или NearestNeighbor в зависимости от масштаба объединенное системы и пользовательского интерфейса.  
  
## Особый случай: prescaling изображений WPF для больших уровней точек на ДЮЙМ  
 Для очень больших масштаба, не кратно 100% \(например, 250%, 350% и так далее\) масштабирование изображений иллюстрациях Бикубический приводит к получению нечеткого, размытый вид пользовательского интерфейса. Впечатление эти изображения наряду с текста почти ничем не отличаются, оптического эффекта. Образы отображаться ближе для глаза, а не в фокусе относительно текста. Результат масштабирования с увеличением размера можно улучшить путем масштабирования изображения с NearestNeighbor наибольшее нескольким 100% \(например, 200% или 300%\) и масштабирование с помощью Бикубический остальной \(дополнительные 50%\).  
  
 Ниже приведен пример различия в результатах, где первое изображение масштабируется с улучшенный алгоритм масштабирование double, 100% \-\> 200% \-\> 250%, а второй только с Бикубический 100% \-\> 250%.  
  
 ![DPI Issues Double Scaling Example](../extensibility/media/dpi-issues-double-scaling-example.png "DPI Issues Double Scaling Example")  
  
 Чтобы включить пользовательский Интерфейс для использования этого масштабирование double, разметки XAML для отображения каждого элемента изображения необходимо изменить. Следующие примеры демонстрируют, как использовать масштабирование double в WPF в Visual Studio с помощью библиотеки DpiHelper и Shell.12\/14.  
  
 Шаг 1: Prescale изображения до 200%, 300% и так далее, с помощью NearestNeighbor.  
  
 Prescale образ с помощью преобразователя, применяется для привязки или с помощью расширения разметки XAML. Пример:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Если образ также должен быть тематические \(многие, если не все, и должно быть\), разметки можно использовать различные преобразователь, выполняющий сначала темы образа, а затем предварительно масштабирования. Можно использовать разметку <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> или <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, в зависимости от вывода требуемое преобразование.  
  
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
  
 Шаг 2: Проверьте правильность конечного размера для текущего DPI.  
  
 Поскольку WPF масштабируется пользовательского интерфейса для текущего DPI, используя свойство BitmapScalingMode UIElement, следует элемент управления Image, с помощью prescaled изображение как его источник будет выглядеть два или три раза больше, чем его. Вот несколько способов для этого счетчика.  
  
-   Если вы знаете измерения исходного изображения в масштабе 100%, можно указать точный размер элемента управления изображения. Эти размеры отразят применяется размер пользовательского интерфейса до масштабирования.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Если размер исходного изображения неизвестен, можно использовать LayoutTransform масштабирование в конечный объект изображения. Пример:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## Включение поддержки HDPI для WebOC  
 По умолчанию элементы управления WebOC \(например, элемент управления WebBrowser в WPF или интерфейс IWebBrowser2\) не позволяют HDPI обнаружения и поддержки. Результат будет внедренный элемент управления содержимым экрана слишком мал, на экране с высоким разрешением. Ниже описывается включение поддержки высокого Разрешения в экземпляре WebOC определенных веб.  
  
 Реализовать интерфейс IDocHostUIHandler \(см. в статье MSDN [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) интерфейс\):  
  
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
  
 При необходимости реализовать интерфейс ICustomDoc \(см. в статье MSDN [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) интерфейс\):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Свяжите класс, реализующий IDocHostUIHandler с документом WebOC. Если реализуется интерфейс ICustomDoc выше, как только свойство WebOC документа является допустимым, привести его к ICustomDoc затем вызовите метод SetUIHandler, передав класс, реализующий IDocHostUIHandler.  
  
```c#  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 Если не реализовал интерфейс ICustomDoc, как только свойство WebOC документа является допустимым, будет необходимо привести его к IOleObject и вызовите метод SetClientSite, передав в класс, реализующий IDocHostUIHandler. Задает флаг DOCHOSTUIFLAG\_DPI\_AWARE DOCHOSTUIINFO, переданный в вызов метода GetHostInfo:  
  
```c#  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 Это должно быть все, что вам необходимо получить управления WebOC должно поддерживать HPDI.  
  
## Советы  
  
1.  При изменении свойства элемента управления WebOC документа, может потребоваться связать документ с помощью класса IDocHostUIHandler.  
  
2.  Если это не поможет, существует известная проблема с WebOC не комплектация Изменение флага точек на ДЮЙМ. Самый надежный способ исправления этого является переключение оптического WebOC смысл два вызова с двумя разными значениями для масштабирования в процентах. Кроме того при необходимости этот обходной путь, возможно, необходимо выполнить его при каждом вызове Навигатор.  
  
    ```c#  
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