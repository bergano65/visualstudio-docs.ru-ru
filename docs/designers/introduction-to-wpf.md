---
title: Введение в WPF
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- csharp
- vb
ms.workload:
- multiple
ms.openlocfilehash: db06323da8ccd3009c52be3ba9dd51478d1d722c
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008464"
---
# <a name="wpf-overview"></a>Общие сведения о WPF

Платформа Windows Presentation Foundation (WPF) позволяет создавать клиентские приложения для настольных систем Windows с привлекательным пользовательским интерфейсом.

![Пример пользовательского интерфейса Contoso Healthcare](../designers/media/wpfintrofigure24.png)

В основе WPF лежит независимый от разрешения векторный модуль визуализации, использующий возможности современного графического оборудования. Возможности этого модуля расширяются с помощью комплексного набора функций разработки приложений, которые включают в себя язык XAML, элементы управления, привязку к данным, макет, двумерную и трехмерную графику, анимацию, стили, шаблоны, документы, мультимедиа, текст и типографические функции. WPF входит в состав .NET Framework, поэтому вы можете создавать приложения, включающие другие элементы библиотеки классов .NET Framework.

Этот обзор предназначен для новичков: в нем рассматриваются ключевые возможности и понятия WPF.

## <a name="program-with-wpf"></a>Программирование с помощью WPF

WPF существует в виде подмножества типов .NET Framework, которые по большей части находятся в пространстве имен <xref:System.Windows> . Если ранее вы создавали приложения с помощью .NET Framework, используя управляемые технологии, такие как ASP.NET и Windows Forms, основные принципы программирования с помощью WPF должны быть вам знакомы: вы создаете экземпляры классов, задаете свойства, вызываете методы и обрабатываете события — все это с использованием своего любимого языка программирования .NET, например C# или Visual Basic.

WPF включает в себя дополнительные конструкции программирования, которые расширяют возможности свойств и событий: [свойства зависимостей](/dotnet/framework/wpf/advanced/dependency-properties-overview) и [перенаправленные события](/dotnet/framework/wpf/advanced/routed-events-overview).

## <a name="markup-and-code-behind"></a>Разметка и код программной части

WPF позволяет разрабатывать приложения, используя как *разметку*, так и *код программной части*, что привычно для разработчиков на ASP.NET. Разметка XAML обычно используется для определения внешнего вида приложения, а управляемые языки программирования (код программной части) — для реализации его поведения. Такое разделение внешнего вида и поведения имеет ряд преимуществ.

- Затраты на разработку и обслуживание снижаются, так как разметка, определяющая внешний вид, не связана тесно с кодом, обуславливающим поведение.

- Повышается эффективность разработки, так как дизайнеры, занимающиеся внешним видом приложения, могут работать параллельно с разработчиками, реализующими поведение приложения.

- [Глобализация и локализация](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview) приложений WPF упрощена.

### <a name="markup"></a>разметку

XAML — это язык разметки на основе XML, который служит для определения внешнего вида приложения в декларативной форме. Обычно он используется для создания окон, страниц и пользовательских элементов управления, а также их заполнения элементами управления, фигурами и графическими элементами.

В приведенном ниже примере XAML используется для определения внешнего вида окна, содержащего одну кнопку.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

Этот код XAML определяет окно и кнопку с помощью элементов `Window` и `Button` соответственно. Каждый элемент настраивается с помощью атрибутов, например атрибута `Window` элемента `Title` , определяющего текст заголовка окна. Во время выполнения WPF преобразует элементы и атрибуты, определенные в разметке, в экземпляры классов WPF. Например, элемент `Window` преобразуется в экземпляр класса <xref:System.Windows.Window> , свойство <xref:System.Windows.Window.Title%2A> которого является значением атрибута `Title` .

На рисунке ниже показан пользовательский интерфейс, который определяется кодом XAML из предыдущего примера.

![Окно с кнопкой](../designers/media/wpfintrofigure10.png)

Так как язык XAML основан на XML, создаваемый с его помощью пользовательский интерфейс образует иерархию вложенных элементов, известную как [дерево элементов](/dotnet/framework/wpf/advanced/trees-in-wpf). Дерево элементов обеспечивает логичный и интуитивно понятный способ создания пользовательских интерфейсов и управления ими.

### <a name="code-behind"></a>Код программной части

При разработке поведения приложения главной задачей является обеспечение реакции на действия пользователя, включая обработку событий (таких как выбор пункта меню или нажатие на кнопку), и вызов в ответ бизнес-логики и логики доступа к данным. В WPF такое поведение реализуется в коде, связанном с разметкой. Этот код называется кодом программной части. В приведенном ниже примере показана обновленная разметка из предыдущего примера и код программной части.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.AWindow"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button" Click="button_Click">Click Me!</Button>

</Window>
```

```csharp
using System.Windows; // Window, RoutedEventArgs, MessageBox 

namespace SDKSample
{
    public partial class AWindow : Window
    {
        public AWindow()
        {
            // InitializeComponent call is required to merge the UI 
            // that is defined in markup with this class, including  
            // setting properties and registering event handlers
            InitializeComponent();
        }

        void button_Click(object sender, RoutedEventArgs e)
        {
            // Show message box when button is clicked
            MessageBox.Show("Hello, Windows Presentation Foundation!");
        }
    }
}
```

```vb
Namespace SDKSample

    Partial Public Class AWindow
        Inherits System.Windows.Window

        Public Sub New()

            ' InitializeComponent call is required to merge the UI 
            ' that is defined in markup with this class, including  
            ' setting properties and registering event handlers
            InitializeComponent()

        End Sub 

        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)

            ' Show message box when button is clicked
            MessageBox.Show("Hello, Windows Presentation Foundation!")

        End Sub 

    End Class 

End Namespace
```

В этом примере в коде программной части реализован класс, производный от класса <xref:System.Windows.Window> . С помощью атрибута `x:Class` разметка связывается с классом в коде программной части. Метод `InitializeComponent` вызывается из конструктора класса кода программной части для слияния пользовательского интерфейса, определенного в разметке, с классом кода программной части. (Метод `InitializeComponent` создается автоматически при сборке приложения, поэтому реализовывать его вручную не нужно.) Сочетание `x:Class` и `InitializeComponent` обеспечивает правильную инициализацию реализации при ее создании. Класс кода программной части также реализует обработчик событий <xref:System.Windows.Controls.Primitives.ButtonBase.Click> кнопки. При нажатии на кнопку обработчик событий выводит окно сообщения, вызывая метод <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> .

На рисунке ниже показан результат нажатия на кнопку.

![MessageBox](../designers/media/wpfintrofigure25.png)

## <a name="controls"></a>Элементы управления

Возможности взаимодействия с пользователем, обеспечиваемые моделью приложения, реализуются с помощью сконструированных элементов управления. В WPF *элемент управления* — это общий термин, который относится к категории классов WPF, размещаемых в окне или на странице, имеющих пользовательский интерфейс и реализующих некоторое поведение.

Более подробную информацию см. в разделе [Элементы управления](/dotnet/framework/wpf/controls/index).

### <a name="wpf-controls-by-function"></a>Функциональная классификация элементов управления WPF

Ниже перечислены встроенные элементы управления WPF.

- **Кнопки**: <xref:System.Windows.Controls.Button> и <xref:System.Windows.Controls.Primitives.RepeatButton>.

- **Вывод данных**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>и <xref:System.Windows.Controls.TreeView>.

- **Вывод и выбор дат**: <xref:System.Windows.Controls.Calendar> и <xref:System.Windows.Controls.DatePicker>.

- **Диалоговые окна**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>и <xref:Microsoft.Win32.SaveFileDialog>.

- **Рукописный ввод**: <xref:System.Windows.Controls.InkCanvas> и <xref:System.Windows.Controls.InkPresenter>.

- **Документы**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>и <xref:System.Windows.Controls.StickyNoteControl>.

- **Ввод**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>и <xref:System.Windows.Controls.PasswordBox>.

- **Макет**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>и <xref:System.Windows.Controls.WrapPanel>.

- **Мультимедиа**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>и <xref:System.Windows.Controls.SoundPlayerAction>.

- **Меню**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>и <xref:System.Windows.Controls.ToolBar>.

- **Навигация**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>и <xref:System.Windows.Controls.TabControl>.

- **Выбор**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>и <xref:System.Windows.Controls.Slider>.

- **Информирование пользователя**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>и <xref:System.Windows.Controls.ToolTip>.

## <a name="input-and-commands"></a>Ввод данных и команды

Элементы управления чаще всего используются для определения ввода данных пользователем и реагирования на него. [Система ввода WPF](/dotnet/framework/wpf/advanced/input-overview) использует как прямые, так и перенаправленные события для поддержки ввода текста, управления фокусом и определения положения указателя мыши.

Приложения часто предъявляют сложные требования к вводу. WPF предоставляет [систему команд](/dotnet/framework/wpf/advanced/commanding-overview), которая отделяет действия по вводу данных пользователем от кода, реагирующего на эти действия.

## <a name="layout"></a>Макет

При создании пользовательского интерфейса вы компонуете элементы управления, настраивая их расположение и размер. Основным требованием любого макета является адаптация к изменениям размеров окна и параметров экрана. Платформа WPF избавляет вас от необходимости писать код для адаптации макета к таким условиям, предоставляя первоклассную расширяемую систему макета.

Ключевым элементом системы макета является относительное позиционирование, которое упрощает адаптацию к меняющимся характеристикам окна и экрана. Кроме того, система макета управляет взаимодействием между элементами управления для определения макета. Взаимодействие протекает в два этапа: сначала элемент управления сообщает родительскому объекту о требуемом расположении и размере, а затем родительский объект сообщает родительскому элементу, какое пространство он может занять.

Система макета доступна дочерним элементам управления посредством базовых классов WPF. Для стандартных макетов, таких как сетка, наложение и закрепление, в WPF имеется несколько элементов управления макетом.

- <xref:System.Windows.Controls.Canvas>: дочерние элементы управления предоставляют собственный макет.

- <xref:System.Windows.Controls.DockPanel>: дочерние элементы управления выравниваются по краям панели.

- <xref:System.Windows.Controls.Grid>: дочерние элементы управления упорядочиваются по строкам и столбцам.

- <xref:System.Windows.Controls.StackPanel>: дочерние элементы управления располагаются с наложением по вертикали или по горизонтали.

- <xref:System.Windows.Controls.VirtualizingStackPanel>: дочерние элементы управления виртуализируются и располагаются в линию по горизонтали или по вертикали.

- <xref:System.Windows.Controls.WrapPanel>: дочерние элементы управления располагаются в порядке слева направо и переносятся на следующую строку, если не помещаются в текущей.

В приведенном ниже примере элемент управления <xref:System.Windows.Controls.DockPanel> используется для размещения нескольких элементов управления <xref:System.Windows.Controls.TextBox> .

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_1.xaml)]

Элемент управления <xref:System.Windows.Controls.DockPanel> позволяет дочерним элементам <xref:System.Windows.Controls.TextBox> сообщать, как они должны быть упорядочены. Для этого в <xref:System.Windows.Controls.DockPanel> реализовано присоединенное свойство `Dock`, которое доступно дочерним элементам управления и позволяет каждому из них указывать стиль закрепления.

> [!NOTE]
> Свойство, которое реализуется родительским элементом управления для использования дочерними элементами, представляет собой конструкцию WPF, называемую [присоединенным свойством](/dotnet/framework/wpf/advanced/attached-properties-overview).

На рисунке ниже показан результат использования разметки XAML из предыдущего примера.

![Страница DockPanel](../designers/media/wpfintrofigure11.png)

## <a name="data-binding"></a>привязка данных,

Большинство приложений предоставляют пользователям возможность просматривать и редактировать данные. Для приложений WPF задачи хранения данных и доступа к ним уже обеспечиваются такими технологиями, как SQL Server и ADO .NET. После получения доступа к данным и их загрузки в управляемые объекты приложения WPF начинается самое сложное. Фактически этот процесс состоит из двух этапов:

1.  копирование данных из управляемых объектов в элементы управления для их отображения и редактирования;

2.  обеспечение копирования изменений, внесенных в данные с помощью элементов управления, обратно в управляемые объекты.

Чтобы упростить разработку приложений, платформа WPF предоставляет механизм привязки данных для автоматического выполнения этих действий. Основной элемент механизма привязки данных — класс <xref:System.Windows.Data.Binding> , задачей которого является привязка элемента управления (целевого объекта привязки) к объекту данных (источнику привязки). Эта связь показана на рисунке ниже.

![Основная схема привязки данных](../designers/media/databindingmostbasic.png)

В следующем примере показано, как привязать элемент управления <xref:System.Windows.Controls.TextBox> к экземпляру пользовательского объекта `Person`. Реализация `Person` показана в следующем коде:

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/VisualBasic/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/CSharp/introduction-to-wpf_2.cs)]

Приведенная ниже разметка привязывает элемент управления <xref:System.Windows.Controls.TextBox> к экземпляру настраиваемого объекта `Person`.

 ```xaml
 <Window
     xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
     xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
     x:Class="SDKSample.DataBindingWindow">

   <!-- Bind the TextBox to the data source (TextBox.Text to Person.Name) -->
   <TextBox Name="personNameTextBox" Text="{Binding Path=Name}" />

 </Window>
 ```

[!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_6.vb)]
[!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_6.cs)]

В этом примере экземпляр класса `Person` создается в коде программной части и устанавливается в качестве контекста данных для `DataBindingWindow`. В разметке свойство <xref:System.Windows.Controls.TextBox.Text%2A> элемента управления <xref:System.Windows.Controls.TextBox> привязывается к свойству `Person.Name` (с помощью синтаксической конструкции «`{Binding ... }`» языка XAML). Этот код XAML предписывает платформе WPF привязать элемент управления <xref:System.Windows.Controls.TextBox> к объекту `Person` , который хранится в свойстве <xref:System.Windows.FrameworkElement.DataContext%2A> окна.

Механизм привязки данных WPF поддерживает дополнительные возможности, включая проверку, сортировку, фильтрацию и группировку. Кроме того, привязка данных поддерживает использование шаблонов данных с целью создания настраиваемого пользовательского интерфейса для связанных данных, если пользовательский интерфейс на основе стандартных элементов управления WPF не удовлетворяет требованиям.

Более подробную информацию см. в разделе [Общие сведения о привязке данных](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="graphics"></a>Графика

Платформа WPF предоставляет широкий, гибкий и масштабируемый набор графических функций, который обладает перечисленными ниже преимуществами.

- **Независимость графики от разрешения и устройства**. Основной единицей измерения в графической системе WPF является аппаратно-независимый пиксель, размер которого составляет 1/96 дюйма вне зависимости от разрешения экрана. Это создает основу для независимой от разрешения и аппаратной платформы отрисовки. Каждый аппаратно-независимый пиксель автоматически масштабируется в соответствии с заданным в системе количеством точек на дюйм (DPI).

- **Повышение точности**. Система координат WPF основана на числах двойной точности с плавающей запятой, а не числах одинарной точности. Значения преобразования и прозрачности также выражаются числами двойной точности. Платформа WPF также поддерживает широкую цветовую палитру (scRGB) и имеет встроенную поддержку управления входными данными из разных цветовых схем.

- **Расширенная поддержка графики и анимации**. Платформа WPF упрощает программирование графики, автоматически управляя анимированными сценами. Вам не нужно беспокоиться об обработке сцен, циклах отрисовки и билинейной интерполяции. Кроме того, WPF обеспечивает поддержку проверки попадания и полную поддержку альфа-версии компоновки.

- **Аппаратное ускорение**. Система графики WPF использует возможности графического оборудования, чтобы снизить нагрузку на ЦП.

### <a name="2d-shapes"></a>Двумерные фигуры

WPF предоставляет библиотеку стандартных векторных двумерных фигур, таких как прямоугольники и эллипсы, которые показаны на рисунке ниже.

![Эллипсы и прямоугольники](../designers/media/wpfintrofigure4.PNG)

Интересной особенностью фигур является то, что они предназначены не только для отображения. В них реализованы многие возможности элементов управления, включая ввод с клавиатуры и с помощью мыши. В приведенном ниже примере показана обработка события <xref:System.Windows.UIElement.MouseUp> объекта <xref:System.Windows.Shapes.Ellipse> .

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_8.cs)]

На рисунке ниже показан результат выполнения предыдущего кода.

![Окно с текстом "you clicked the ellipse&#33;"](../designers/media/wpfintrofigure12.png)

Более подробную информацию см. в разделе [Обзор фигур и базовых средств рисования в приложении WPF](/dotnet/framework/wpf/data/data-binding-overview).

### <a name="2d-geometries"></a>Двумерные геометрические объекты

Двумерные фигуры, предоставляемые WPF, включают в себя стандартный набор базовых фигур. Однако вам может потребоваться создать собственные фигуры, чтобы упростить разработку пользовательского интерфейса. Для этой цели WPF предоставляет геометрические объекты. На рисунке ниже демонстрируется использование геометрических объектов для создания пользовательской фигуры, которую можно нарисовать напрямую, применять как кисть или использовать для обрезки других фигур и элементов управления.

Объекты<xref:System.Windows.Shapes.Path> можно использовать для рисования замкнутых и незамкнутых фигур, нескольких фигур и даже криволинейных фигур.

Объекты <xref:System.Windows.Media.Geometry> можно использовать для обрезки, проверки попадания и отрисовки двумерных графических данных.

![Различные способы использования Path](../designers/media/wpfintrofigure5.png)

Дополнительные сведения см. в разделе [Общие сведения о классе Geometry](/dotnet/framework/wpf/graphics-multimedia/geometry-overview).

### <a name="2d-effects"></a>Двумерные эффекты

В число возможностей двумерной графики WPF входят визуальные эффекты, такие как градиенты, растровые изображения, рисунки, рисование с видео, вращение, масштабирование и наклон. Применение всех этих эффектов обеспечивается с помощью кистей. На рисунке ниже показан ряд примеров.

![Иллюстрация различных кистей](../designers/media/wpfintrofigure6.png)

Дополнительные сведения см. в разделе [Общие сведения о кистях WPF](/dotnet/framework/wpf/graphics-multimedia/wpf-brushes-overview).

### <a name="3d-rendering"></a>Трехмерная отрисовка

Платформа WPF также предоставляет возможности трехмерной отрисовки, которые интегрированы с возможностями двумерной графики, что позволяет создавать более интересные и яркие пользовательские интерфейсы. Например, на рисунке ниже показаны двумерные изображения, наложенные на трехмерные объекты.

![Снимок экрана примера Visual3D](../designers/media/wpfintrofigure13.png)

Дополнительные сведения см. в статье [Обзор трехмерной графики](/dotnet/framework/wpf/graphics-multimedia/3-d-graphics-overview).

## <a name="animation"></a>Анимация

Поддержка анимации в WPF позволяет применять к элементам управления такие эффекты, как увеличение, дрожание, вращение и исчезание, создавать интересные эффекты смены страниц и другие эффекты. Вы можете анимировать большинство классов WPF, даже настраиваемые классы. На рисунке ниже показана простая анимация в действии.

![Изображения анимированного куба](../designers/media/wpfintrofigure7.png)

Дополнительные сведения см. в разделе [Общие сведения об эффектах анимации](/dotnet/framework/wpf/graphics-multimedia/animation-overview).

## <a name="media"></a>Мультимедиа

Одни из способов передачи более информативного содержимого — использовать аудиовизуальные средства. WPF обеспечивает специальную поддержку изображений, видео и звука.

### <a name="images"></a>Изображения

Изображения присутствуют в большинстве приложений, и платформа WPF предоставляет несколько способов их использования. На рисунке ниже показан пользовательский интерфейс со списком, содержащим эскизы. При выборе эскиза изображение отображается в полном размере.

![Эскизы и полноразмерное изображение](../designers/media/wpfintrofigure8.png)

Дополнительные сведения см. в разделе [Общие сведения об обработке изображений](/dotnet/framework/wpf/graphics-multimedia/imaging-overview).

### <a name="video-and-audio"></a>Видео и звук

Элемент управления <xref:System.Windows.Controls.MediaElement> позволяет воспроизводить как видео, так и звук и достаточно гибок для того, чтобы служить основой для пользовательского мультимедиапроигрывателя. Приведенная ниже разметка XAML реализует мультимедиапроигрыватель.

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_9.xaml)]

На рисунке ниже показано окно с элементом управления <xref:System.Windows.Controls.MediaElement> в действии.

![Элемент управления MediaElement с аудио и видео](../designers/media/wpfintrofigure1.png)

Дополнительные сведения см. в разделе [Графика и мультимедиа](/dotnet/framework/wpf/graphics-multimedia).

## <a name="text-and-typography"></a>Текст и типографическая разметка

Чтобы упростить высококачественную отрисовку текста, платформа WPF предоставляет следующие возможности:

- поддержка шрифтов OpenType;

- усовершенствования ClearType;

- высокая производительность за счет аппаратного ускорения;

- интеграция текста с мультимедиа, графикой и анимацией;

- поддержка международных шрифтов и резервных механизмов.

В качестве демонстрации интеграции текста с графикой на рисунке ниже показано применение эффектов оформления текста.

![Текст с различными украшениями](../designers/media/wpfintrofigure23.png)

Более подробную информацию см. в разделе [Типографическая разметка в Windows Presentation Foundation](/dotnet/framework/wpf/advanced/typography-in-wpf).

## <a name="customize-wpf-apps"></a>Настройка приложений WPF

До сих пор мы рассматривали основные строительные блоки WPF для разработки приложений. Для размещения и предоставления содержимого приложения, состоящего в основном из элементов управления, используется модель приложения. Для упрощения размещения элементов управления в пользовательском интерфейсе и сохранения их компоновки в случае изменения размера окна или параметров экрана используется система макета WPF. Так как большинство приложений предоставляют пользователям возможность взаимодействовать с данными, для сокращения объема работы, необходимой для интеграции пользовательского интерфейса с данными, используется привязка данных. Чтобы улучшить внешний вид приложения, используется широкий ряд средств графики, анимации и мультимедиа, предоставляемый платформой WPF.

Однако зачастую этих основных средств недостаточно для создания уникального и визуально привлекательного пользовательского интерфейса. Стандартные элементы управления WPF могут не сочетаться с требуемым оформлением вашего приложения. Данные могут отображаться не самым эффективным образом. Пользовательскому интерфейсу вашего приложения может в целом не подходить внешний вид тем Windows по умолчанию. Наряду с другими типами расширяемости, технологии представления во многих случаях требуется визуальная расширяемость.

По этой причине WPF предоставляет разнообразные механизмы создания уникальных пользовательских интерфейсов, включая модель мультимедийного содержимого для элементов управления, триггеры, шаблоны элементов управления и данных, стили, ресурсы пользовательского интерфейса, темы и обложки.

### <a name="content-model"></a>Модель содержимого

Основным назначением большинства элементов управления WPF является отображение содержимого. В WPF тип и число элементов, составляющих содержимое элемента управления, называются *моделью содержимого*элемента управления. Некоторые элементы могут содержать только один объект и только один тип содержимого. Например, содержимым элемента управления <xref:System.Windows.Controls.TextBox> является строковое значение, присвоенное свойству <xref:System.Windows.Controls.TextBox.Text%2A> . В приведенном ниже примере задается содержимое элемента управления <xref:System.Windows.Controls.TextBox>.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

На рисунке ниже показан результат.

![Элемент управления TextBox с текстом](../designers/media/wpfintrofigure21.png)

Другие элементы управления, однако, могут содержать несколько объектов с различным типом содержимого. Содержимым элемента управления <xref:System.Windows.Controls.Button>, определяемым свойством <xref:System.Windows.Controls.ContentControl.Content%2A>, могут быть различные объекты, в том числе элементы управления макетом, текст, изображения и фигуры. В приведенном ниже примере показан элемент управления <xref:System.Windows.Controls.Button> , содержащий <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border>и <xref:System.Windows.Controls.MediaElement>.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ButtonContentWindow"
    Title="Button Content">

  <Button Margin="20">
    <!-- Button Content -->
    <DockPanel Width="200" Height="180">
      <Label DockPanel.Dock="Top" HorizontalAlignment="Center">Click Me!</Label>
      <Border Background="Black" BorderBrush="Yellow" BorderThickness="2"
        CornerRadius="2" Margin="5">
        <MediaElement Source="media/wpf.wmv" Stretch="Fill" />
      </Border>
    </DockPanel>
  </Button>
</Window>
```

На рисунке ниже показано содержимое этой кнопки.

![Кнопка с множественными типами содержания](../designers/media/wpfintrofigure22.png)

Дополнительную информацию о типах содержимого, поддерживаемого различными элементами управления, см. в разделе [Модель содержимого WPF](/dotnet/framework/wpf/controls/wpf-content-model).

### <a name="triggers"></a>Триггеры

Хотя основным назначением разметки XAML является определение внешнего вида приложения, ее также можно использовать для реализации некоторых аспектов поведения приложения. Один из примеров — изменение внешнего вида приложения с помощью триггеров при выполнении пользователем определенных действий. Дополнительные сведения см. в разделе [Стилизация и использование шаблонов](/dotnet/framework/wpf/controls/styling-and-templating).

### <a name="control-templates"></a>Шаблоны элементов управления

Пользовательские интерфейсы по умолчанию для элементов управления WPF обычно формируются на основе других элементов управления и фигур. Например, элемент управления <xref:System.Windows.Controls.Button> состоит из элементов управления <xref:Microsoft.Windows.Themes.ButtonChrome> и <xref:System.Windows.Controls.ContentPresenter> . <xref:Microsoft.Windows.Themes.ButtonChrome> обеспечивает стандартный внешний вид кнопки, а <xref:System.Windows.Controls.ContentPresenter> служит для вывода ее содержимого, определяемого свойством <xref:System.Windows.Controls.ContentControl.Content%2A> .

Иногда внешний вид элемента управления по умолчанию может не согласовываться с общим оформлением приложения. В этом случае можно использовать <xref:System.Windows.Controls.ControlTemplate> для изменения пользовательского интерфейса элемента управления, не меняя его содержимое и поведение.

Например, в приведенном ниже примере показано, как изменить внешний вид элемента управления <xref:System.Windows.Controls.Button> с помощью <xref:System.Windows.Controls.ControlTemplate>.

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_17.vb)]

В этом примере пользовательский интерфейс кнопки по умолчанию заменяется элементом <xref:System.Windows.Shapes.Ellipse> , имеющим темно-синюю границу и заполнение, определяемое <xref:System.Windows.Media.RadialGradientBrush>. В элементе управления <xref:System.Windows.Controls.ContentPresenter> выводится содержимое элемента <xref:System.Windows.Controls.Button>— текст «Click Me!» При нажатии на элемент <xref:System.Windows.Controls.Button> по-прежнему вызывается событие <xref:System.Windows.Controls.Primitives.ButtonBase.Click> , что соответствует поведению элемента управления <xref:System.Windows.Controls.Button> по умолчанию. Результат показан на рисунке ниже.

![Кнопка в виде эллипса и второе окно](../designers/media/wpfintrofigure2.png)

### <a name="data-templates"></a>Шаблоны данных

В то время как шаблон элемента управления позволяет определять внешний вид элемента управления, шаблон данных дает возможность настраивать оформление его содержимого. Шаблоны данных часто используются для оптимизации отображения привязанных данных. На рисунке ниже показано стандартное оформление элемента управления <xref:System.Windows.Controls.ListBox>, привязанного к коллекции объектов `Task`, в котором у каждой задачи есть название, описание и приоритет.

![Список с видом по умолчанию](../designers/media/wpfintrofigure18.png)

Оформление по умолчанию является стандартным для элемента управления <xref:System.Windows.Controls.ListBox>. Однако оно предполагает, что для каждой задачи отображается только ее название. Чтобы отобразить название, описание и приоритет задачи, нужно изменить оформление по умолчанию для элементов списка, привязанных к элементу управления <xref:System.Windows.Controls.ListBox> , с помощью <xref:System.Windows.DataTemplate>. Приведенный ниже код XAML определяет такой шаблон <xref:System.Windows.DataTemplate>, который применяется к каждой задаче с помощью атрибута <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> .

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="SDKSample.DataTemplateWindow"
  Title="With a Data Template">
  <Window.Resources>
    <!-- Data Template (applied to each bound task item in the task collection) -->
    <DataTemplate x:Key="myTaskTemplate">
      <Border Name="border" BorderBrush="DarkSlateBlue" BorderThickness="2"
        CornerRadius="2" Padding="5" Margin="5">
        <Grid>
          <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
          </Grid.RowDefinitions>
          <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition />
          </Grid.ColumnDefinitions>
          <TextBlock Grid.Row="0" Grid.Column="0" Padding="0,0,5,0" Text="Task Name:"/>
          <TextBlock Grid.Row="0" Grid.Column="1" Text="{Binding Path=TaskName}"/>
          <TextBlock Grid.Row="1" Grid.Column="0" Padding="0,0,5,0" Text="Description:"/>
          <TextBlock Grid.Row="1" Grid.Column="1" Text="{Binding Path=Description}"/>
          <TextBlock Grid.Row="2" Grid.Column="0" Padding="0,0,5,0" Text="Priority:"/>
          <TextBlock Grid.Row="2" Grid.Column="1" Text="{Binding Path=Priority}"/>
        </Grid>
      </Border>
    </DataTemplate>
  </Window.Resources>

  <!-- UI -->
  <DockPanel>
    <!-- Title -->
    <Label DockPanel.Dock="Top" FontSize="18" Margin="5" Content="My Task List:"/>

    <!-- Data template is specified by the ItemTemplate attribute -->
    <ListBox
      ItemsSource="{Binding}"
      ItemTemplate="{StaticResource myTaskTemplate}"
      HorizontalContentAlignment="Stretch"
      IsSynchronizedWithCurrentItem="True"
      Margin="5,0,5,5" />

 </DockPanel>
</Window>
```

На рисунке ниже показан результат использования этого кода.

![Список, использующий шаблон данных](../designers/media/wpfintrofigure19.png)

Обратите внимание на то, что элемент управления <xref:System.Windows.Controls.ListBox> сохранил свое поведение и общий внешний вид. Изменилось только оформление содержимого, отображаемого в списке.

Дополнительные сведения см. в разделе [Общие сведения о шаблонах данных](/dotnet/framework/wpf/data/data-templating-overview).

### <a name="styles"></a>Стили

Стили позволяют разработчикам и дизайнерам стандартизировать внешний вид своего продукта. Платформа WPF предоставляет строгую модель стилей, в основе которой лежит элемент <xref:System.Windows.Style> . В приведенном ниже примере создается стиль, который задает `Orange` в качестве цвета фона для каждого элемента управления <xref:System.Windows.Controls.Button> в окне.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.StyleWindow"
    Title="Styles">
  <!-- Style that will be applied to all buttons -->
  <Style TargetType="{x:Type Button}">
    <Setter Property="Background" Value="Orange" />
    <Setter Property="BorderBrush" Value="Crimson" />
    <Setter Property="FontSize" Value="20" />
    <Setter Property="FontWeight" Value="Bold" />
    <Setter Property="Margin" Value="5" />
  </Style>
  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>

  <!-- This label will not have the style applied to it -->
  <Label>Don't Click Me!</Label>

  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>
</Window>
```

Так как этот стиль предназначен для всех элементов управления <xref:System.Windows.Controls.Button>, он автоматически применяется ко всем кнопкам в окне, как показано на рисунке ниже.

![Две оранжевые кнопки](../designers/media/wpfintrofigure20.png)

Дополнительные сведения см. в разделе [Стилизация и использование шаблонов](/dotnet/framework/wpf/controls/styling-and-templating).

### <a name="resources"></a>Ресурсы

Элементы управления в приложении должны иметь одинаковое оформление, которое может включать любые элементы: от шрифтов и цвета фона до шаблонов элементов управления, шаблонов данных и стилей. Благодаря поддержке ресурсов пользовательского интерфейса в WPF можно инкапсулировать эти ресурсы в одном месте для повторного использования.

В приведенном ниже примере определяется общий цвет фона для элементов управления <xref:System.Windows.Controls.Button> и <xref:System.Windows.Controls.Label>.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ResourcesWindow"
    Title="Resources Window">

  <!-- Define window-scoped background color resource -->
  <Window.Resources>
    <SolidColorBrush x:Key="defaultBackground" Color="Red" />
  </Window.Resources>

  <!-- Button background is defined by window-scoped resource -->
  <Button Background="{StaticResource defaultBackground}">One Button</Button>

  <!-- Label background is defined by window-scoped resource -->
  <Label Background="{StaticResource defaultBackground}">One Label</Label>
</Window>
```

Ресурс цвета фона реализуется с помощью элемента свойства `Window.Resources`. Этот ресурс доступен всем дочерним элементам объекта <xref:System.Windows.Window>. Существует ряд различных областей действия ресурсов. Некоторые из них перечислены ниже в порядке их разрешения.

1.  Отдельный элемент управления (с использованием наследуемого свойства <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> ).

2.  <xref:System.Windows.Window> или <xref:System.Windows.Controls.Page> (также с использованием наследуемого свойства <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> ).

3.  <xref:System.Windows.Application> (с использованием свойства <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> ).

Разнообразие областей действия обеспечивает гибкость в отношении способов определения ресурсов и предоставления доступа к ним.

Помимо прямого сопоставления ресурсов с определенной областью действия, можно упаковать один или несколько ресурсов с помощью отдельного объекта <xref:System.Windows.ResourceDictionary> , на который можно ссылаться в других частях приложения. Так, в приведенном ниже примере определяется цвет фона по умолчанию в библиотеке ресурсов.

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

 В приведенном ниже примере используется ссылка на библиотеку ресурсов, определенную в предыдущем примере, что позволяет использовать ее в рамках всего приложения.

```xaml
<Application
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.App">

  <Application.Resources>
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="BackgroundColorResources.xaml"/>
      </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
  </Application.Resources>
</Application>
```

Ресурсы и словари ресурсов лежат в основе реализованной в WPF поддержки тем и обложек.

Дополнительные сведения см. в статье [Ресурсы](/dotnet/framework/wpf/advanced/xaml-resources).

### <a name="custom-controls"></a>Пользовательские элементы управления

Хотя WPF предоставляет множество возможностей настройки, могут возникнуть ситуации, когда существующие элементы управления WPF не удовлетворяют потребности вашего приложения или его пользователей. Это может произойти в указанных ниже случаях.

- Требуемый пользовательский интерфейс нельзя создать, настроив внешний вид существующих элементов, реализованных в WPF.

- Требуемое поведение не поддерживается существующими элементами, реализованными в WPF, или его поддержка представляет трудность.

В такой ситуации вы можете воспользоваться одной из трех моделей WPF, чтоб создать новый элемент управления. Каждая модель предназначена для определенного сценария и предполагает, что пользовательский элемент управления наследуется от определенного базового класса WPF. Ниже перечислены эти три модели.

- **Модель пользовательского элемента управления**. Пользовательский элемент управления наследуется от <xref:System.Windows.Controls.UserControl> и составляется из одного или нескольких других элементов управления.

- **Модель элемента управления**. Пользовательский элемент управления наследуется от <xref:System.Windows.Controls.Control> и используется для создания реализаций, в которых поведение и внешний вид разделяются с помощью шаблонов, как в большинстве элементов управления WPF. Наследование от класса <xref:System.Windows.Controls.Control> обеспечивает большую гибкость при создании собственного пользовательского интерфейса, чем пользовательские элементы управления, но может потребовать больших усилий.

- **Модель элемента платформы**. Пользовательский элемент управления наследуется от класса <xref:System.Windows.FrameworkElement> , если его внешний вид определяется пользовательской логикой отрисовки, а не шаблонами.

В приведенном ниже примере показан пользовательский элемент управления для увеличения или уменьшения числового значения, наследуемый от <xref:System.Windows.Controls.UserControl>.

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/CSharp/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/VisualBasic/introduction-to-wpf_34.vb)]

В следующем примере показан код XAML, необходимый для включения пользовательского элемента управления в <xref:System.Windows.Window>.

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](../designers/codesnippet/Xaml/introduction-to-wpf_37.xaml)]

На рисунке ниже показан элемент управления `NumericUpDown`, размещенный в окне <xref:System.Windows.Window>.

![Настраиваемый UserControl](../designers/media/wpfintrofigure3.png)

Дополнительные сведения о пользовательских элементах управления см. в разделе [Общие сведения о разработке управления](/dotnet/framework/wpf/controls/control-authoring-overview).

## <a name="wpf-best-practices"></a>Рекомендации по использованию WPF

Как и любую другую платформу разработки, WPF можно использовать разными способами для получения нужного результата. Чтобы ваши приложения WPF обеспечивали требуемый уровень удобства и отвечали потребностям пользователей в целом, следует придерживаться рекомендаций в отношении специальных возможностей, глобализации, локализации и производительности. Дополнительные сведения:

- [Специальные возможности](/dotnet/framework/ui-automation/accessibility-best-practices)
- [Глобализация и локализация WPF](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview)
- [Производительность приложения WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)
- [Безопасность WPF](/dotnet/framework/wpf/security-wpf)

## <a name="next-steps"></a>Следующие шаги

Мы рассмотрели основные возможности WPF. Теперь пора приступить к созданию первого приложения WPF.

> [!div class="nextstepaction"]
> [Пошаговое руководство. Создание первого классического приложения WPF](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)

## <a name="see-also"></a>См. также

- [Начало работы с WPF](../designers/getting-started-with-wpf.md)
- [Windows Presentation Foundation](/dotnet/framework/wpf/index)
- [Ресурсы сообщества по WPF](/dotnet/framework/wpf/getting-started/community-feedback)
