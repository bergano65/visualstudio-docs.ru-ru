---
title: Решение вопросов ДОИ2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80f16c5b17a41d1f95b9bcb70e90eb8de46ad69d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740103"
---
# <a name="address-dpi-issues"></a>Решение проблем ДОИ
Все большее число устройств поставляются с экранами с высоким разрешением. Эти экраны, как правило, имеют более 200 пикселей на дюйм (ppi). Работа с приложением на этих компьютерах потребует масштабирования содержимого для удовлетворения потребностей при просмотре содержимого на обычном расстоянии просмотра устройства. По состоянию на 2014 год основной мишенью для дисплеев высокой плотности являются мобильные вычислительные устройства (планшеты, ноутбуки и телефоны).

Windows 8.1 и выше содержит несколько функций, позволяющих этим машинам работать с дисплеями и средами, где машина прикрепляется как к дисплеям высокой плотности, так и к стандартной плотности одновременно.

- Windows позволяет масштабировать содержимое устройства с помощью настройки "Сделать текст и другие элементы больше или меньше" (доступно с Windows XP).

- Windows 8.1 и выше автоматически масштабируют содержимое для большинства приложений, чтобы быть последовательными при перемещении между дисплеями различной плотности пикселей. Когда основной дисплей имеет высокую плотность (200% масштабирования), а вторичный дисплей - стандартную плотность (100%), Windows автоматически масштабирует содержимое окна приложения на вторичном дисплее (1 пиксель отображается на каждые 4 пикселя, отображаемые приложением).

- Windows будет по умолчанию в правильном масштабировании для плотности пикселей и расстояния просмотра для дисплея (Windows 7 и выше, OEM-настраиваемый).

- Windows может автоматически масштабировать содержимое до 250% на новых устройствах, превышающей 280 ppi (по состоянию на Windows 8.1 S14).

  Windows имеет способ борьбы с расширением uI, чтобы воспользоваться увеличением количества пикселей. Приложение выбирает в этой системе, объявив себя "система DPI известно". Приложения, которые этого не делают, масштабируются системой. Это может привести к "нечеткой" пользовательский опыт, когда все приложение равномерно пиксель нойсеньки растягивается. Пример:

  ![Проблемы с четкостью DPI](../extensibility/media/dpi-issues-fuzzy.png "Проблемы с четкостью DPI")

  Visual Studio выбирает в том, чтобы быть DPI масштабирования осведомлены, и, следовательно, не является "виртуализированным".

  Windows (и Visual Studio) используют несколько технологий uI, которые имеют различные способы борьбы с факторами масштабирования, установленными системой. Пример:

- WPF измеряет управление независимым способом (единицы, а не пиксели). UI WPF автоматически масштабируется для текущего DPI.

- Все размеры текста независимо от рамок UI выражены в точках, и поэтому рассматриваются системой как независимые от DPI. Текст в Win32, WinForms и WPF уже правильно масштабируется при нарисованном на устройстве отображения.

- Диалоги и окна Win32/WinForms имеют средства для включения макета, который изменяет размер текста (например, через панели сетки, потока и таблицы). Они позволяют избежать жестких пикселей, которые не масштабируются при увеличении размеров шрифта.

- Иконки, предоставляемые системой, или ресурсы, основанные на системных метриках (например, SM_CXICON и SM_CXSMICON), уже масштабируются.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Старый Win32 (GDI, GDI) и UI, основанный на WinForms
В то время как WPF уже является высоким dPI-известно, большая часть нашего Win32 / GDI основе кода не была первоначально написана с DPI осведомленности в виду. Windows предоставила API-аПУЛ. Исправления проблем Win32 должны использовать их последовательно по всему продукту. Visual Studio предоставила библиотеку класса помощников, чтобы избежать дублирования функциональности и обеспечения согласованности продукта.

## <a name="high-resolution-images"></a>Изображения с высоким разрешением
Этот раздел в первую очередь для разработчиков расширения Visual Studio 2013. Для Visual Studio 2015 используйте сервис изображений, который встроен в Visual Studio. Вы также можете обнаружить, что вам нужно поддерживать / целевой много версий Visual Studio и, следовательно, с помощью службы изображения в 2015 году не вариант, поскольку он не существует в предыдущих версиях. Этот раздел также для вас тогда.

## <a name="scaling-up-images-that-are-too-small"></a>Масштабирование изображений, которые слишком малы
Изображения, которые слишком малы, могут быть масштабированы и отображаются на GDI и WPF с помощью некоторых распространенных методов. Управляемые классы помощников DPI доступны внутренним и внешним интеграторам Visual Studio для решения проблем, связанных с иконками масштабирования, бит-картами, изображениями и имиджевыми списками. На основе Win32 на основе C / C-хаперы доступны для масштабирования HICON, HBITMAP, HIMAGELIST, и VsUI::GdiplusImage. Масштабирование битовой карты обычно требует изменения только в одной строке после включения ссылки на библиотеку-помощник. Пример:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

Масштабирование списка изображений зависит от того, завершен ли список изображений во время загрузки или приложен во время выполнения. Если вы полнить во `LogicalToDeviceUnits()` время загрузки, позвоните с изображением, как вы бы bitmap. Когда коду необходимо загрузить индивидуальную битовую карту перед составлением списка изображений, не забудьте масштабировать размер изображения в списке изображений:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

В родном коде размеры могут быть уменьшены при создании списка изображений следующим образом:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Функции в библиотеке позволяют указать алгоритм повторного определения размера. При масштабировании изображений, которые будут размещены в imagelists, не забудьте указать цвет фона, который используется для прозрачности, или использовать Ближайшее масштабирование (что вызовет искажения на 125% и 150%).

Проконсультируйтесь с документацией <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> по MSDN.

В следующей таблице приведены примеры того, как изображения должны масштабироваться на соответствующих факторах масштабирования ДОИ. Изображения, изложенные в оранжевом обозначают нашу передовую практику по состоянию на Visual Studio 2013 (100%-200% DPI масштабирования):

![Масштабирование в проблемах с DPI](../extensibility/media/dpi-issues-scaling.png "Масштабирование в проблемах с DPI")

## <a name="layout-issues"></a>Проблемы с выкладкой
Общие проблемы компоновки можно избежать в первую очередь путем сохранения точек в маштаберуем и по отношению друг к другу, а не с помощью абсолютных местоположений (в частности, в единицах пикселей). Пример:

- Позиции layout/text необходимо настроить с учетом уменьшенных изображений.

- Столбцы в сетках должны иметь ширину, скорректированную для уменьшенного текста.

- Также необходимо будет увеличить масштабирование размеров или пространства между элементами. Размеры, основанные только на измерениях текста, как правило, в порядке, поскольку шрифты автоматически масштабируются.

  Функции помощника доступны <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> в классе, позволяющие масштабировать сяоку X и Y:

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (функции позволяют масштабироваться на оси X/Y)

- int-пространство - DpiHelper.LogicalToDeviceUnitsX (10);

- высота - VsUI::DpiHelper::LogicalToDeviceUnitsY (5);

  Есть LogicalToDeviceUnits перегрузки, чтобы позволить масштабирования объектов, таких как Rect, Point, и размер.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Использование библиотеки/класса DPIHelper для масштабирования изображений и макета
Библиотека помощника Visual Studio DPI доступна в родных и управляемых формах и может использоваться за пределами оболочки Visual Studio другими приложениями.

Чтобы воспользоваться библиотекой, перейдите в [Visual Studio VSSDK и](https://github.com/Microsoft/VSSDK-Extensibility-Samples) клонируйте образец High-DPI_Images_Icons.

В исходных файлах включите *VsUIDpiHelper.h* и позвоните в статические функции `VsUI::DpiHelper` класса:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> Не используйте функции помощника в статических переменных уровня модуля или класса. Библиотека также использует статические для синхронизации потоков, и вы можете столкнуться с проблемами инициализации заказов. Либо преобразуйте эти статические в нестатические переменные, либо оберните их в функцию (чтобы они были построены на первом доступе).

Чтобы получить доступ к функциям помощника DPI из управляемого кода, который будет работать внутри среды Visual Studio:

- Проект потребления должен ссылаться на последнюю версию MPF Shell. Пример:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Убедитесь, что проект имеет ссылки на **System.Windows.Forms**, **PresentationCore**, и **PresentationUI**.

- В коде используйте пространство имен **Microsoft.VisualStudio.PlatformUI** и позвоните в статические функции класса DpiHelper. Для поддерживаемых типов (точек, размеров, прямоугольников и т.д.) предусмотрены функции расширения, которые возвращают новые масштабированные объекты. Пример:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Работа с нечеткостью изображений WPF в масштабируемом uI
В WPF бит-карты автоматически переизбираются WPF для текущего уровня dPI зумса с использованием высококачественного бикубического алгоритма (по умолчанию), который хорошо работает для фотографий или больших скриншотов, но не подходит для значков элементов меню, поскольку он вводит воспринимаемую нечеткость.

Рекомендации

- Для изображения логотипа и баннеров можно использовать режим повторного размера по умолчанию. <xref:System.Windows.Media.BitmapScalingMode>

- Для элементов меню и <xref:System.Windows.Media.BitmapScalingMode> изображений иконографии следует использовать, если это не вызывает других искажений артефактов для устранения нечеткости (на 200% и 300%).

- Для больших уровней масштабирования не кратные 100% (например, 250% или 350%), масштабирование иконографических изображений с бикубической приводит к нечеткой, вымытой uI. Лучший результат получается путем первого масштабирования изображения с NearestNeighbor до самого большого кратного 100% (например, 200% или 300%) и масштабирование с bicubic оттуда. Для получения дополнительной информации см.

  Класс DpiHelper в пространстве имен Microsoft.VisualStudio.PlatformUI <xref:System.Windows.Media.BitmapScalingMode> предоставляет участника, который может быть использован для связывания. Это позволит оболочке Visual Studio управлять режимом масштабирования биткарты по продукту равномерно, в зависимости от фактора масштабирования DPI.

  Чтобы использовать его в XAML, добавьте:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

Оболочка Visual Studio уже устанавливает это свойство на окнах верхнего уровня и диалогах. UI, работающий в Visual Studio, уже унаследует его. Если параметр не распространяется на определенные элементы uI, он может быть установлен на корневом элементе UI XAML/WPF. Места, где это происходит включают всплывающие окна, на элементы с Win32 родителей, и дизайнер окна, которые иссякнут процесса, таких как Blend.

Некоторые uI может масштабироваться независимо от системного уровня DPI, например, редактора текста Visual Studio и разработчиков на базе WPF (WPF Desktop и Windows Store). В этих случаях, DpiHelper.BitmapScalingMode не должны использоваться. Чтобы устранить эту проблему в редакторе, команда IDE создала пользовательское свойство под названием RenderOptions.BitmapScalingMode. Установите это значение свойства на высококачественное или ближайшее соседое в зависимости от комбинированного уровня масштабирования системы и вашего uI.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Особый случай: предмасштабирование изображений WPF для больших уровней ДОИ
Для очень больших уровней зума, которые не являются кратными 100% (например, 250%, 350% и так далее), масштабирование изображений иконографии с бикубической приводит к нечеткой, вымываются UI. Впечатление от этих изображений наряду с четким текстом почти как у оптической иллюзии. Изображения, как представляется, ближе к глазу и не в фокусе по отношению к тексту. Результат масштабирования при таком увеличенном размере можно улучшить путем первого масштабирования изображения с ближайшим соседом до самого большого кратного 100% (например, 200% или 300%) и масштабирование с бикубической до оставшейся части (дополнительные 50%).

Ниже приводится пример различий в результатах, где первое изображение масштабируется с улучшенным алгоритмом двойного масштабирования 100%->200%->250%, а второе только с бикубической 100%->250%.

![Пример двойного масштабирования DPI](../extensibility/media/dpi-issues-double-scaling-example.png "Пример двойного масштабирования DPI")

Для того, чтобы можно было использовать этот двойной масштабирование, необходимо изменить разметку XAML для отображения каждого элемента изображения. Ниже приведены следующие примеры, как использовать двойное масштабирование в WPF в Visual Studio с помощью библиотеки DpiHelper и Shell.12/14.

Шаг 1: Предварительное изображение до 200%, 300%, и так далее с помощью Ближайшего соседа.

Предварительно масштабируйте изображение с помощью конвертера, применяемого на привязке, либо с расширением разметки XAML. Пример:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Если изображение также должно быть тематическим (большинство, если не все, должны), разметка может использовать другой конвертер, который сначала делает theming изображения, а затем предварительного масштабирования. Наценка может <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> использоваться как <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>один или, в зависимости от желаемого вывода преобразования.

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

Шаг 2: Убедитесь, что окончательный размер является правильным для текущего ДОИ.

Поскольку WPF будет масштабировать uI для текущего DPI с помощью свойства BitmapScalingMode, установленного на UIElement, управление изображениями с использованием заранее масштабируемого изображения, поскольку его источник будет выглядеть в два или три раза больше, чем следовало бы. Ниже приведены несколько способов противодействия этому эффекту:

- Если вы знаете размер исходного изображения на 100%, вы можете указать точный размер элемента управления изображения. Эти размеры будут отражать размер uI до нанесения масштабирования.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Если размер исходного изображения неизвестен, layoutTransform может быть использован для масштабирования конечного объекта изображения. Пример:

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
По умолчанию элементы управления WebOC (например, управление WebBrowser в WPF или интерфейс IWebBrowser2) не позволяют обнаружить и поддерживать HDPI. Результатом будет встроенный элемент управления с содержанием дисплея, который слишком мал на дисплее с высоким разрешением. Ниже описывается, как включить поддержку с высоким DPI в определенном экземпляре WebOC.

Реализация интерфейса IDocHostUIHandler (см. статью MSDN на [IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85)):

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

Дополнительно реализуйте интерфейс ICustomDoc (см. статью MSDN на [ICustomDoc:](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85))

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

Связать класс, который реализует IDocHostUIHandler с документом WebOC. Если вы реализовали интерфейс ICustomDoc выше, то, как только свойство документа WebOC является действительным, отбросьте его в ICustomDoc и позвоните в метод SetUIHandler, пройдя класс, который реализует IDocHostUIHandler.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

Если вы не реализовали интерфейс ICustomDoc, то, как только свойство документа WebOC является действительным, вам нужно `SetClientSite` будет бросить его в IOleObject, и вызвать метод, проходя в классе, который реализует IDocHostUIHandler. Установите DOCHOSTUIFLAG_DPI_AWARE флаг на DOCHOSTUIINFO, передаваемом к вызову метода: `GetHostInfo`

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

Это должно быть все, что вам нужно, чтобы получить контроль WebOC для поддержки HPDI.

## <a name="tips"></a>Советы

1. Если свойство документа в элементе управления WebOC изменяется, возможно, потребуется переанификировать документ с классом IDocHostUIHandler.

2. Если вышеперечисленное не работает, существует известная проблема с WebOC не поднимая изменения на флаг DPI. Самый надежный способ исправить это заключается в переключении оптического зума WebOC, то есть двух вызовов с двумя разными значениями для процента масштабирования. Кроме того, если требуется этот обходной путь, возможно, потребуется выполнить его на каждом вызове навигации.

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
