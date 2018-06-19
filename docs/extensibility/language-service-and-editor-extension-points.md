---
title: Служба языка и точек расширения редактора | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d3c253ba52da1fd6bb9133e44ba6858e8f1a4151
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148602"
---
# <a name="language-service-and-editor-extension-points"></a>Служба языка и точек расширения редактора
Редактор предоставляет точки расширения, которые можно расширить как части компонента Managed Extensibility Framework (MEF), включая большинство возможностей службы языка. Они перечислены категории точки основным расширением.  
  
-   Типы содержимого  
  
-   Классификация типы и форматы классификации  
  
-   Поля и полосы прокрутки  
  
-   Теги  
  
-   Украшения  
  
-   Процессоры мыши  
  
-   Обработчики перетаскивания  
  
-   Параметры  
  
-   IntelliSense  
  
## <a name="extending-content-types"></a>Расширение типов содержимого  
 Типы содержимого являются определениями типов тексту, обрабатываемому в редакторе, например, «текст», «код» или «CSharp». Определить новый тип содержимого, объявив переменную типа <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> и предоставляя новый тип содержимого, уникальное имя. Чтобы зарегистрировать тип содержимого с помощью редактора, его необходимо экспортируйте вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute> — Имя типа содержимого.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> — Имя типа содержимого, из которого создается данный тип содержимого. Тип содержимого может наследовать от нескольких типов содержимого.  
  
 Поскольку <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> класс запечатан, можно экспортировать его без параметра типа.  
  
 В следующем примере показано атрибуты экспорта в определении типа содержимого.  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 Типы содержимого могут основываться на ноль или более существующих типов содержимого. Существуют следующие встроенные типы:  
  
-   Любое: базовый тип содержимого. Родительский объект для всех типов содержимого.  
  
-   Текст: базовый тип содержимого не проекции. Наследует от «любой».  
  
-   Открытого текста: для текста, не содержащих кода. Наследует от «text».  
  
-   Кода: код всех типов. Наследует от «text».  
  
-   Вставить: исключает текст из любого типа обработки. Текст с данным типом содержимого никогда не будет иметь любое расширение, применяемый к нему.  
  
-   Проекция: для содержимого буферов проекции. Наследует от «любой».  
  
-   IntelliSense: для содержимого IntelliSense. Наследует от «text».  
  
-   Sighelp: Справка по сигнатурам. Наследует от «intellisense».  
  
-   Sighelp-doc: подпись справочной документации. Наследует от «intellisense».  
  
 Вот некоторые типы содержимого, которые определены в Visual Studio и в некоторых языках, размещенным в Visual Studio:  
  
-   Basic  
  
-   C/C++  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   FindResults  
  
-   F#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 Для получения списка доступных типов контента, импортировать <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, который поддерживает коллекцию типов содержимого для редактора. Следующий код импортирует этой службы как свойство.  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 Чтобы связать тип содержимого с расширением имени файла, используйте <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>.  
  
> [!NOTE]
>  Расширения имен файлов в Visual Studio, зарегистрированных с помощью <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> на языкового пакета службы. <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> Сопоставляется тип содержимого MEF расширение имени файла, которое было зарегистрировано таким образом.  
  
 Чтобы экспортировать определение типа содержимого расширение имени файла, необходимо включить следующие атрибуты:  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: указывает расширение имени файла.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: Указывает тип содержимого.  
  
 Поскольку <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> класс запечатан, можно экспортировать его без параметра типа.  
  
 В следующем примере показано атрибуты экспорта на расширение имени файла в определение типа содержимого.  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> Управляет связи между расширения имен файлов и типов содержимого.  
  
## <a name="extending-classification-types-and-classification-formats"></a>Расширение категории и классификации форматы  
 Типы классификации можно использовать для определения вида текста, для которого вы хотите предоставить различной обработки (например, выделение цветом зеленый синий текст «ключевое слово» и «комментарий»). Определите новый тип классификации, объявив переменную типа <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> и предоставляя ему уникальное имя.  
  
 Чтобы зарегистрировать тип классификации с помощью редактора, экспортируйте его вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя типа классификации.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: имя типа классификации, от которого наследует этот тип классификации. Все типы классификации наследовать от «text», а тип классификации может наследовать от нескольких других типов классификации.  
  
 Поскольку <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> класс запечатан, можно экспортировать его без параметра типа.  
  
 В следующем примере показано атрибуты экспорта в определении типа классификации.  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> Предоставляет доступ к стандартным классификациям. Типы встроенных классификации включают эти:  
  
-   "текст"  
  
-   «естественного языка» (является производным от «text»)  
  
-   (является производным от «text») «формальный язык»  
  
-   «string» (является производным от «literal»)  
  
-   «character» (является производным от «literal»)  
  
-   «Числовой» (является производным от «literal»)  
  
 Наследовать набор различные типы ошибок <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>. Они включают следующие типы ошибок.  
  
-   «Синтаксическая ошибка»  
  
-   «Ошибка компилятора»  
  
-   «Ошибка других»  
  
-   «Предупреждение»  
  
 Для получения списка доступных типов классификации, импортировать <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, который поддерживает коллекцию типов классификации для редактора. Следующий код импортирует этой службы как свойство.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 Определение формата классификации можно определить для нового типа классификации. Производный класс <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> и экспортировать его с типом <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя формата.  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: отображаемое имя формата.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Указывает, отображается ли в формате **шрифты и цвета** страница **параметры** диалоговое окно.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: приоритет формата. Допустимые значения: от <xref:Microsoft.VisualStudio.Text.Classification.Priority>.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: Введите имя классификации сопоставить этот формат.  
  
 В следующем примере показано атрибуты экспорта для определения формата классификации.  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 Для получения списка доступных форматов, импортировать <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, которая поддерживает набор форматов для редактора. Следующий код импортирует этой службы как свойство.  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## <a name="extending-margins-and-scrollbars"></a>Расширение поля и полосы прокрутки  
 Поля и полосы прокрутки — это элементы основного представления редактора Помимо самого представления текста. Можно указать любое количество полей, помимо стандартных полей, отображаемых вокруг представления текста.  
  
 Реализуйте <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> интерфейс для определения полей. Необходимо также реализовать <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> интерфейс для создания поля.  
  
 Регистрация поставщика margin в редакторе, необходимо экспортировать поставщика вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя поля.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: порядок, в котором отображается поле, относительно других полей.  
  
     Существуют следующие встроенные поля:  
  
    -   «Полоса прокрутки по горизонтали Wpf»  
  
    -   «Полоса прокрутки по вертикали Wpf»  
  
    -   «Число поля строки Wpf»  
  
     Горизонтальная поля, имеющие атрибут порядок `After="Wpf Horizontal Scrollbar"` отображаются под встроенные поля, а горизонтальная поля, имеющие атрибут порядок `Before ="Wpf Horizontal Scrollbar"` отображаются над встроенные поля. Правой вертикальной рамки, которые имеют атрибут порядок `After="Wpf Vertical Scrollbar"` отображаются в правой части полосы прокрутки. Осталось вертикальной рамки, которые имеют атрибут порядок `After="Wpf Line Number Margin"` отображаться слева от поле номеров строк (Если отображается).  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: тип поля (слева, справа, сверху или снизу).  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, «текст» или «код»), для которого действителен на поле.  
  
 В следующем примере показано атрибуты экспорта в поставщике поля для поля, которое отображается в правой части поле номеров строк.  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extending-tags"></a>Расширение тегов  
 Теги — это способ сопоставления данных с различных видов текста. Во многих случаях связанных данных отображается в виде визуальный эффект, но не все теги имеют визуальное представление. Можно определить собственные типа тегов путем реализации <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Необходимо также реализовать <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> для предоставления теги для данного набора фрагментов текста и <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> для предоставления разметчика. Необходимо экспортировать поставщика разметчика вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, «текст» или «код»), для которой ваш тег является допустимым.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: тип тега.  
  
 В следующем примере показано атрибуты экспорта на поставщика разметчика.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Следующие виды тег являются встроенными:  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: связанные с <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: связанные с типами ошибок.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: связанные с элемент оформления.  
  
    > [!NOTE]
    >  Пример <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, см. Определение HighlightWordTag в [Пошаговое руководство: выделение текста](../extensibility/walkthrough-highlighting-text.md).  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: связанные с областями, которые можно разворачивать и сворачивать в создания структуры.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: Определяет элемент оформления занимает пространство в представлении текста. Дополнительные сведения о согласовании пространства оформлений в следующем разделе.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: предоставляет автоматические интервалы и его изменение для оформления.  
  
 Поиск и использование тегов для буферов и представлений, Импорт <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> или <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, который позволяет <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> запрошенного типа. Следующий код импортирует этой службы как свойство.  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>Теги и MarkerFormatDefinitions  
 Вы можете расширить <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> класса, чтобы определить внешний вид тег. Необходимо экспортировать класс (как <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя, используемое для ссылки на этот формат  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: в результате форматирования для отображения в пользовательском Интерфейсе  
  
 В конструкторе необходимо указать отображаемое имя и внешний вид тега. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> Определяет цвет заливки и <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> определяет цвет границы. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> Локализуемое имя определение формата.  
  
 Ниже приведен пример определения формата:  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
[UserVisible(true)]  
internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
{  
    public HighlightWordFormatDefinition()  
    {  
        this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";   
        this.ZOrder = 5;  
    }  
}  
  
```  
  
 Чтобы применить это определение формата в тег, ссылаться на имя, заданные в атрибут имени класса (не отображаемое имя).  
  
> [!NOTE]
>  Пример <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, см. класс HighlightWordFormatDefinition в [Пошаговое руководство: выделение текста](../extensibility/walkthrough-highlighting-text.md).  
  
## <a name="extending-adornments"></a>Расширение украшения  
 Украшения определить визуальные эффекты, которые можно добавить любой текст, который отображается в виде текста или к тексту Просмотр сам. Можно определить собственные оформления в качестве любого типа <xref:System.Windows.UIElement>.  
  
 В классе оформления, необходимо объявить <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Чтобы зарегистрировать макете оформления, экспортируйте его вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя элемента оформления.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: упорядочение оформления относительно других слоев оформления. Класс <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> определяет четыре уровня по умолчанию: выбор, структура, курсор и текста.  
  
 В следующем примере показано атрибуты экспорта в определении слой оформления.  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 Необходимо создать второй класс, реализующий <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> и обрабатывает его <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> событий путем создания экземпляра оформления. Необходимо экспортировать этот класс вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, «текст» или «код»), для которого действителен оформления.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: тип представления текста, для которого действителен этот оформления. Класс <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> имеет набор предопределенных ролей представления текста. Например <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> в основном используется для представления текста из файлов. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> используется для представления текста, что пользователь может изменить или перемещаться с помощью мыши и клавиатуры. Примеры <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> представления: представление текстового редактора и **вывода** окна.  
  
 В следующем примере показано атрибуты экспорта на поставщике оформления.  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 Оформления то, которое занимает пространство на том же уровне, как текст. Для создания такого рода оформления, необходимо определить класс тег, который наследует от <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, который определяет объем пространства, занимаемого оформления.  
  
 Как и все элементы оформления, необходимо экспортировать определение слой оформления.  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 Чтобы создать оформления уровня, необходимо создать класс, реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, помимо класс, реализующий <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (как и другие виды оформлений).  
  
 Чтобы зарегистрировать поставщика разметчика, его необходимо экспортировать вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, «текст» или «код»), для которого действителен вашей оформления.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: тип представления текста, для которого данный тег или оформления является допустимым. Класс <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> имеет набор предопределенных ролей представления текста. Например <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> в основном используется для представления текста из файлов. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> используется для представления текста, что пользователь может изменить или перемещаться с помощью мыши и клавиатуры. Примеры <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> представления: представление текстового редактора и **вывода** окна.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: тип тега или оформления, который вы определили. Необходимо добавить второй <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> для <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.  
  
 В следующем примере показано атрибуты экспорта поставщика разметчика для оформления тег уровня.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>Расширение мыши процессоров  
 Можно добавить специальную обработку для ввода мыши. Создайте класс, наследующий от <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> и переопределение событий мыши для входных данных, которые требуется обработать. Необходимо также реализовать <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> в второго класса и экспортировать его вместе с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> , указывающий тип содержимого (например, «текст» или «код»), для которого действителен обработчика мыши.  
  
 В следующем примере показано атрибуты экспорта в поставщике мыши процессора.  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extending-drop-handlers"></a>Расширение обработчики перетаскивания  
 Можно настроить поведение обработчиков drop для определенных типов текста, создав класс, реализующий <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> и второй класс, реализующий <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> Создание обработчик перетаскивания. Необходимо экспортировать обработчик перетаскивания, а также следующие атрибуты:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: текстовый формат, для которого действителен этот обработчик перетаскивания. Следующие форматы обрабатываются в порядке приоритета от самого высокого до самого низкого:  
  
    1.  Любой пользовательский формат  
  
    2.  FileDrop  
  
    3.  EnhancedMetafile  
  
    4.  WaveAudio  
  
    5.  RIFF  
  
    6.  Dif  
  
    7.  Языковой стандарт  
  
    8.  Палитра  
  
    9. PenData  
  
    10. Сериализуемые  
  
    11. SymbolicLink  
  
    12. XAML  
  
    13. XamlPackage  
  
    14. TIFF  
  
    15. Bitmap  
  
    16. DIB  
  
    17. MetafilePicture  
  
    18. CSV  
  
    19. System.String  
  
    20. Формат HTML  
  
    21. UnicodeText  
  
    22. OEMText  
  
    23. Text  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя обработчик перетаскивания.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: упорядочение обработчик перетаскивания до или после обработчик перетаскивания по умолчанию. Обработчик перетаскивания по умолчанию для Visual Studio называется «DefaultFileDropHandler».  
  
 В следующем примере показано атрибуты экспорта в поставщике обработчик перетаскивания.  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>Расширение параметров редактора  
 Можно определить параметры допустимы только в определенной области, например, в виде текста. Редактор предоставляет этот набор стандартных параметров: параметры редактора, просмотрите параметры и параметры просмотра Windows Presentation Foundation (WPF). Эти параметры можно найти в <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, и <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.  
  
 Чтобы добавить новый параметр, создайте класс, производный от одного из этих классов определение параметров:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 В следующем примере показано, как для экспорта определения параметра, который имеет логическое значение.  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extending-intellisense"></a>Расширение IntelliSense  
 IntelliSense — это общий термин для групп компонентов, которые предоставляют сведения о структурированных текстовых и завершение операторов для него. Эти возможности включают завершение операторов, Справка по сигнатурам, краткие сведения и лампочки. Завершение операторов помогает пользователям правильно введите ключевое слово или члена имя языка. Справка по сигнатурам отображает подпись или подписи для метода, который пользователь ввел только. Краткие сведения отображаются Полная сигнатура, имя типа или члена при наведении указателя мыши на нем. Лампочка предоставляют дополнительные действия для идентификаторов, определенных в определенных контекстах, например, переименование всех вхождений переменной после переименования одно вхождение.  
  
 Структура функции IntelliSense во многом одинаков во всех случаях:  
  
-   IntelliSense *broker* отвечает за общий процесс.  
  
-   IntelliSense *сеанса* представляет последовательность событий между вызывающей срабатывание триггера средстве и фиксации или отмены выделения. Сеанс обычно инициируется некоторые жест пользователя.  
  
-   IntelliSense *контроллера* отвечает за определение время начала и окончания сеанса. Также определяет, когда данные должна быть зафиксирована и при отмене сеанса.  
  
-   IntelliSense *источника* предоставляет содержимое и решает наилучшее соответствие.  
  
-   IntelliSense *докладчика* отвечает за отображение содержимого.  
  
 В большинстве случаев рекомендуется ввести по крайней мере источника и контроллер. Можно также предоставить докладчика, если вы хотите настроить отображение.  
  
### <a name="implementing-an-intellisense-source"></a>Реализация источника IntelliSense  
 Чтобы настроить источник, необходимо реализовать один (или более) источника следующие интерфейсы:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> рекомендуется к использованию для <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
 Кроме того необходимо реализовать поставщик одного типа:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> рекомендуется к использованию для <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.  
  
 Необходимо экспортировать поставщика вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя источника.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, «текст» или «код»), к которому относится источник.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: порядок, в которых должен отображаться источнику (в отношении других источников).  
  
-   В следующем примере показано атрибуты экспорта в поставщике источника завершения.  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 Дополнительные сведения о реализации IntelliSense источников см. в следующих пошаговых руководствах:  
  
 [Пошаговое руководство. Отображение всплывающих подсказок для кратких сведений](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Пошаговое руководство. Отображение справки сигнатуры](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Пошаговое руководство. Отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implementing-an-intellisense-controller"></a>Реализация контроллер IntelliSense  
 Чтобы настроить контроллер, необходимо реализовать <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> интерфейса. Кроме того необходимо реализовать поставщиком контроллера вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя контроллера.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, «текст» или «код»), к которому применяется контроллера.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: порядок отображения контроллер должен (в отношении других контроллеров).  
  
 В следующем примере показано атрибуты экспорта в поставщике контроллера завершения.  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 Дополнительные сведения об использовании IntelliSense контроллеров см. в следующих пошаговых руководствах:  
  
 [Пошаговое руководство. Отображение всплывающих подсказок для кратких сведений](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)