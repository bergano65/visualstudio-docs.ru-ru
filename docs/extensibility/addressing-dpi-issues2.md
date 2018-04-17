---
title: Адресация DPI Issues2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc0801d3fb43188ac3371ed7e5e7394b0e3aad72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="addressing-dpi-issues"></a>Решение проблем точек на ДЮЙМ
При увеличении числа устройств входят в состав «с высоким разрешением» экранов. Обычно эти окна имеют более чем 200 точек на дюйм (ppi). Для работы с приложением на этих компьютерах потребуется содержимое для масштабируемых в соответствии с потребностями просмотра содержимого на расстоянии обычный режим просмотра для устройства. Начиная с 2014 основной целевой высокой плотности отображения на мобильных устройств (планшетных ПК, ноутбуки лотке и телефоны).  
  
 Windows 8.1 и более поздних версий содержит несколько функций, чтобы включить эти машины для работы с отображает и средах, где машина подключена к обеим версиям с высокой плотностью и отображает плотность standard в то же время.  
  
-   Windows может позволяют масштабировать содержимое к устройству с помощью «сделать текст и другие элементы больше или меньше» (доступным, начиная с Windows XP).  
  
-   Windows 8.1 и более поздних версиях автоматически масштабируется содержимого для большинства приложений для согласования при перемещении между отображением разные плотности пикселей. Когда основного монитора является высокая плотность (200% масштабирование) и получателей отображается стандартный плотность (100%), Windows будет автоматически масштабировать содержимое окна приложения с экрана получателя (отображаются для каждого 4 пикселя, подготовки к просмотру в 1 пиксель приложение).  
  
-   Windows по умолчанию право масштабирования для плотности пикселей, а также просмотр расстояния для отображения (Windows 7 и выше, можно настроить OEM).  
  
-   Windows можно автоматически масштабировать содержимого вверх до 250% на новых устройствах, которые превышают 280 ppi (начиная с Windows 8.1 S14).  
  
 В Windows есть способ работы с вертикальное масштабирование пользовательского интерфейса, чтобы воспользоваться преимуществами повышения пикселей счетчиков. Приложение позволяет использовать эту систему, объявив сам «system ДЮЙМ». Приложений, которые не масштабируются в системе. Это может привести к «Нечеткое» пользователей, где все приложение равномерно увеличить пикселей. Пример:  
  
 ![Точек на ДЮЙМ выдает Нечеткое](../extensibility/media/dpi-issues-fuzzy.png "выдает Нечеткое точек на ДЮЙМ")  
  
 Visual Studio позволяет использовать, поддерживающего масштабирование DPI и таким образом не «виртуализируется.»  
  
 Windows (и Visual Studio) используют несколько технологий пользовательского интерфейса, которые имеют разные способы работы с системой коэффициенты масштабирования. Пример:  
  
-   WPF меры элементов управления в аппаратно независимым способом (единицы, не в пикселах). Пользовательский Интерфейс WPF автоматически масштабируется для текущего Разрешения.  
  
-   Все размеры текста независимо от того, структура пользовательского интерфейса выражаются в пунктах и таким образом, обрабатываются системой как зависящая от Разрешения. Текст в Win32, WPF и WinForms уже масштаб правильно при выводе устройства отображения.  
  
-   Win32/WinForms диалоговые окна и окна имеют средство включения макет, изменять размеры текст — например, через сетку, поток и панели макета таблицы. С их помощью жестко пикселей расположений, которые не масштабируется при увеличении размеров шрифта как избежать.  
  
-   Значки, предоставляемые системой или ресурсам на основании метрик системы (например, SM_CXICON и SM_CXSMICON) уже масштабировать в сторону.  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Более старые Win32 (GDI, GDI +) и пользовательский Интерфейс на базе WinForms  
 Хотя WPF высокой дюйм, большая часть наш код на основе Win32/GDI не было записано изначально с учета DPI в виду. Windows предоставляет API-интерфейсы масштабированием DPI. Исправления проблем Win32 следует использовать постоянно по продукту. Visual Studio предоставляет вспомогательный класс библиотеки классов, чтобы избежать дублирования функциональности и обеспечение согласованности с продуктом.  
  
## <a name="high-resolution-images"></a>Изображения с высоким разрешением  
 Этот раздел предназначен главным образом для разработчиков, расширение Visual Studio 2013. Для Visual Studio 2015 используют службу образов, который встроен в Visual Studio. Кроме того, возможно, необходимые для поддержки и целевого многие версий Visual Studio, и таким образом с помощью служба образов в 2015 вариант невозможен, так как он не существует в предыдущих версиях. В этом разделе будет также автоматически.  
  
## <a name="scaling-up-images-that-are-too-small"></a>Вертикальное масштабирование изображений, которые слишком велики  
 Образы, которые слишком малы можно «масштабировать в сторону» и отображается GDI и WPF с помощью некоторых распространенных методов. Вспомогательные классы управляемых точек на ДЮЙМ, доступных для внутренних и внешних интеграторами Visual Studio масштабирование значки, растровые изображения, imagestrips и imagelists адрес. На базе Win32 собственного C / C ++ вспомогательных методов, доступных для масштабирования HICON, HBITMAP, HIMAGELIST и VsUI::GdiplusImage. Только масштабирование растрового изображения обычно требует изменения одной строки после ссылки на вспомогательную библиотеку. Пример:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Масштабирование изображений зависит от ли imagelist выполнена во время загрузки или добавляется во время выполнения. Если полные во время загрузки, вызовите LogicalToDeviceUnits() с imagelist, как растровое изображение. Когда код необходимо загрузить отдельных точечный рисунок до составление imagelist, убедитесь, что масштабировать размер изображений imagelist:  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 В машинном коде можно масштабировать измерений при создании imagelist следующим образом:  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Функции в библиотеке разрешается указывать алгоритм изменения размера. Когда масштабирования изображения следует поместить в imagelists, убедитесь в том задать цвет фона, используемый для прозрачности или использовать NearestNeighbor масштабирование (что приведет к искажения на 125% и 150%).  
  
 Обратитесь к <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> документации в библиотеке MSDN.  
  
 Ниже приведены примеры как образы масштабироваться соответствующих точек на дюйм коэффициенты масштабирования. Образы зеленым цветом обозначения наши рекомендации, начиная с Visual Studio 2013 (100-200% масштабирование):  
  
 ![Масштабирование в проблемах с DPI](../extensibility/media/dpi-issues-scaling.png "масштабирование в проблемах с DPI")  
  
## <a name="layout-issues"></a>Проблемы с макетом  
 Распространенные проблемы с макетом можно избежать, в первую очередь, оставив установленным точек, в пользовательском Интерфейсе масштабируется, так и относительно друг друга, а не с помощью абсолютного расположения (в частности, в единицах пикселей). Пример:  
  
-   Для настройки учетной записи для масштабированных изображения должны позиций макета или текст.  
  
-   Должно быть масштабированных текста с учетом ширины столбцов в сетке.  
  
-   Жестко запрограммированный размер или расстояние между элементами также необходимо масштабировать в сторону увеличения. Размеры, которые основаны только на размеры текста обычно работают нормально, поскольку шрифты автоматически масштабировать в сторону.  
  
 Вспомогательные функции доступны в <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> класс, позволяющий масштабирования по оси X и Y:  
  
-   LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (разрешить функции масштабирования в X и оси Y)  
  
-   int пространства = DpiHelper.LogicalToDeviceUnitsX (10);  
  
-   Высота int = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);  
  
 Существуют перегрузки LogicalToDeviceUnits, чтобы разрешить масштабирование объекты, такие как Rect, точки и размер.  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>С помощью библиотеки DPIHelper или класс для масштабирования изображения и макет  
 Вспомогательную библиотеку Visual Studio DPI доступен в машинном и управляемом формах и может использоваться другими приложениями за пределами оболочки Visual Studio.  
  
 Для использования библиотеки, перейдите к [примеры расширяемости Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) и клонирования высокой DPI_Images_Icons образца  
  
 В файлах исходного кода содержит VsUIDpiHelper.h и вызывать статические функции VsUI::DpiHelper класса:  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  Не используйте вспомогательные функции в статических переменных уровня класса или модуля. Библиотека также использует статистику для синхронизации потоков и может выполняться в порядке инициализации неполадки. Преобразуйте эти статических переменных в нестатических-переменных членов, либо помещать их в функцию (то есть они конструировать при первом доступе).  
  
 Для доступа к DPI вспомогательных функций из управляемого кода, который будет выполняться в среде Visual Studio:  
  
-   Много проекта должен ссылаться на последнюю версию MPF оболочки. Пример:  
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Убедитесь, проект содержит ссылки на **System.Windows.Forms**, **PresentationCore**, и **PresentationUI**.  
  
-   В коде используйте **Microsoft.VisualStudio.PlatformUI** пространство имен и вызова статических функций DpiHelper класса. Для поддерживаемых типов (точек, размеры, прямоугольники и т. д.), предоставляемые функции расширения, которые возвращают новые масштабирование объектов. Пример:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Работа с WPF разброс изображения в масштабируемым пользовательского интерфейса  
 В WPF растровые изображения изменяется автоматически в WPF для текущего уровня масштабирования точек на ДЮЙМ, с помощью алгоритма Бикубический высокого качества (по умолчанию), который хорошо подходит для изображения или больших снимки экрана, но не подходит для значки элементов меню, так как она порождает предполагаемых разброс .  
  
 Рекомендации:  
  
-   Для логотипа изображения и ленты графический объект, значение по умолчанию <xref:System.Windows.Media.BitmapScalingMode> можно использовать режим изменения размера.  
  
-   Пункты меню и образы иллюстрациях <xref:System.Windows.Media.BitmapScalingMode> следует использовать, если оно не вызывает другие артефакты искажения во избежание потере четкости (в 200% и 300%).  
  
-   Для масштабирования больших уровней не кратно 100% (например, 250% или 350%), масштабирование изображений иллюстрациях с Бикубический приводит Нечеткое, подложки пользовательского интерфейса. Наилучшего результата получается путем масштабирования изображения с NearestNeighbor для наибольшего кратно 100% (например, 200% или 300%) и масштабирование с Бикубический оттуда. В разделе особый случай: prescaling изображений WPF для больших DPI уровни для получения дополнительной информации.  
  
 Класс DpiHelper в пространстве имен Microsoft.VisualStudio.PlatformUI предоставляет элемент <xref:System.Windows.Media.BitmapScalingMode> может использоваться для привязки. Он позволяет оболочке Visual Studio для управления точечного рисунка масштабирование режим с продуктом одинаково, в зависимости от коэффициента масштабирования точек на ДЮЙМ.  
  
 Чтобы использовать его в XAML, добавьте следующую команду:  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Оболочка Visual Studio уже устанавливает это свойство для окон верхнего уровня и диалоговых окон. Пользовательский Интерфейс на основе WPF в Visual Studio уже наследует его. Если параметр не распространяется на определенной части пользовательского интерфейса, его можно задать в корневом элементе пользовательского интерфейса XAML и WPF. Окружение, в котором это происходит, включают всплывающих окон для элементов, имеющих родителей Win32, и конструктора окон, которые запускаются из процесса, такими как Blend.  
  
 Пользовательский Интерфейс можно масштабировать независимо от уровня масштабирования точек на ДЮЙМ набор системы, например редактор текста Visual Studio и конструкторах на основе WPF (WPF рабочий стол и магазин Windows). В этих случаях DpiHelper.BitmapScalingMode использовать не следует. Чтобы устранить эту проблему в редакторе, команда интегрированной среды разработки, создать пользовательское свойство под названием RenderOptions.BitmapScalingMode. Установите это значение свойства HighQuality или NearestNeighbor в зависимости от того, объединенные масштаб системы и пользовательского интерфейса.  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Особым случаем: prescaling изображений WPF для больших уровней точек на ДЮЙМ  
 Для очень больших масштаба, не кратно 100% (например, 250% 350% и т. д) масштабирование изображений иллюстрациях Бикубический приводит к получению Нечеткое, подложки пользовательского интерфейса. Впечатление эти образы вместе с текстом четкое почти ничем не отличаются, иллюзии оптические. То изображения появляются более низких для глаза, а не в фокусе относительно текста. Результат масштабирования на этот увеличивать размер можно повысить путем масштабирования изображения с NearestNeighbor для наибольшего кратно 100% (например, 200% или 300%) и масштабирование с Бикубический остальной (на 50%).  
  
 Ниже приведен пример различия в результатах, где первое изображение масштабируется алгоритму улучшенное масштабирование двойной 100% -> 200% -> 250%, а второй только с Бикубический 100% -> 250%.  
  
 ![Точек на ДЮЙМ выдает двойные масштабирования пример](../extensibility/media/dpi-issues-double-scaling-example.png "двойные масштабирования пример выдает точек на ДЮЙМ")  
  
 Чтобы включить пользовательский Интерфейс для использования этого масштабирование double, разметки XAML для отображения каждого элемента изображения необходимо будет изменить. Следующие примеры демонстрируют использование двойной масштабирование в WPF в Visual Studio с помощью библиотеки DpiHelper и Shell.12/14.  
  
 Шаг 1: Prescale изображения до 200% 300% и так далее с помощью NearestNeighbor.  
  
 Prescale образ с помощью преобразователя, реализованной в привязке, или с использованием расширения разметки XAML. Пример:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Если изображения также должен быть включен в тему (многие, если не все, должно быть), разметку может использовать преобразователь другой, сначала выполняющий темы изображения, а затем предварительно масштабирования. Разметка можно использовать любой <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> или <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, в зависимости от выходных данных требуемое преобразование.  
  
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
  
 Так как WPF масштабируется пользовательского интерфейса для текущего DPI, используя свойство BitmapScalingMode элементов пользовательского интерфейса, должен быть элемента управления Image, с помощью prescaled образа, как его источника будут выглядеть два или три раза больше, чем его. Ниже приведены несколько способов счетчика этот эффект.  
  
-   Если вы знаете измерения исходного изображения в масштабе 100%, можно указать точный размер элемента управления изображения. Эти размеры отразят применяется размер пользовательского интерфейса, перед масштабированием.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Если известен размер исходного изображения, LayoutTransform можно масштабировать результирующий объект изображения. Пример:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>Включение поддержки HDPI WebOC  
 По умолчанию элементы управления WebOC (например, элемент управления WebBrowser в WPF или интерфейс IWebBrowser2) не позволяют HDPI обнаружения и поддержки. Это приведет к появлению внедренный элемент управления содержимым экрана слишком малое с высоким разрешением экрана. Ниже описано, как для включения поддержки высоким Разрешением в экземпляре WebOC конкретных web.  
  
 Реализуйте интерфейс IDocHostUIHandler (см. в статье MSDN [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) интерфейса):  
  
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
  
 При необходимости реализовать интерфейс ICustomDoc (см. в статье MSDN [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) интерфейса):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Свяжите класс, реализующий IDocHostUIHandler с WebOC документа. Если реализован интерфейс ICustomDoc выше, затем сразу свойство документа WebOC действителен, приведите его к ICustomDoc и вызовите метод SetUIHandler, передав класс, реализующий IDocHostUIHandler.  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 Если не реализовал интерфейс ICustomDoc, затем сразу WebOC свойство документа является допустимым, необходимо выполнить его приведение к IOleObject и вызовите метод SetClientSite, передав в класс, реализующий IDocHostUIHandler. Установите флаг DOCHOSTUIFLAG_DPI_AWARE на DOCHOSTUIINFO, переданного в вызов метода GetHostInfo:  
  
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
  
 Это должна быть все, что нужно получить управления WebOC должно поддерживать HPDI.  
  
## <a name="tips"></a>Советы  
  
1.  При изменении свойства документа в элементе управления WebOC, может потребоваться повторное связывание документа с классом IDocHostUIHandler.  
  
2.  Если вышеперечисленное не работает, имеется известная проблема с WebOC, не получает Изменение флага точек на ДЮЙМ. Самый надежный способ исправления этого является для переключения оптические масштаб WebOC значения двух вызовов с двумя разными значениями для масштабирования в процентах. Кроме того при необходимости этот обходной путь, он может потребоваться выполнить эту процедуру при каждом вызове Навигатор.  
  
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