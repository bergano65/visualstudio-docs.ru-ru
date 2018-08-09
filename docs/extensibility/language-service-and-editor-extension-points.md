---
title: Языковая служба и точки расширения редактора | Документация Майкрософт
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
ms.openlocfilehash: 88ec5affddb814e350b2edbab7b44efc95371bff
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639767"
---
# <a name="language-service-and-editor-extension-points"></a>Точки расширения редактора и служба языка
Редактор предоставляет точки расширения, которые можно использовать как части Managed Extensibility Framework (MEF) компонентов, включая большинство функций службы языка. Ниже приведены категории точки основным расширением.  
  
-   Типы содержимого  
  
-   Классификация типов и форматов классификации  
  
-   Поля и полосы прокрутки  
  
-   Теги  
  
-   Элементы оформления  
  
-   Мыши процессоров  
  
-   Обработчики перетаскивания  
  
-   Параметры  
  
-   IntelliSense  
  
## <a name="extend-content-types"></a>Расширения типов содержимого  
 Типы содержимого являются определениями типов текста, обрабатываемых редактором, например, «text», «код» или «C#». Определение нового типа содержимого путем объявления переменной типа <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> и предоставляя новый тип содержимого, уникальное имя. Чтобы зарегистрировать тип содержимого с помощью редактора, его нужно экспортируйте вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute> — Имя типа содержимого.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> — Имя типа содержимого, производным которого является данный тип содержимого. Тип содержимого могут наследовать несколько типов содержимого.  
  
 Так как <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> запечатанный класс, можно экспортировать его без параметра типа.  
  
 В следующем примере показано атрибутов экспорта на определение типа содержимого.  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 Типы содержимого могут основываться на ноль или более существующих типов содержимого. Ниже приведены встроенные типы.  
  
-   Любой: базовый тип содержимого. Родительский объект для всех типов содержимого.  
  
-   Текст: базовый тип содержимого не проекции. Наследует от «любой».  
  
-   В виде обычного текста: для текста не кода. Наследует от «text».  
  
-   Код: для кода всех видов. Наследует от «text».  
  
-   Вставить: исключает любые виды обработки текста. Текст данным типом содержимого никогда не будет иметь любое расширение, примененных к нему.  
  
-   Проекция: для содержимого буферов проекции. Наследует от «любой».  
  
-   IntelliSense: для содержимого IntelliSense. Наследует от «text».  
  
-   Sighelp: Справка по сигнатурам. Наследует от «intellisense».  
  
-   Sighelp-doc: подпись справочной документации. Наследует от «intellisense».  
  
 Ниже приведены некоторые типы содержимого, которые определены в Visual Studio и некоторых языках, размещенных в Visual Studio.  
  
-   Basic  
  
-   C/C++  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   Результатов поиска  
  
-   F#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 Для обнаружения списка доступных типов контента, импортировать <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, который поддерживает коллекцию типов содержимого для редактора. Следующий код импортирует эту службу как свойство.  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 Чтобы связать тип содержимого с расширением имени файла, используйте <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>.  
  
> [!NOTE]
>  В Visual Studio, расширения имен файлов регистрируются с помощью <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> о пакете службы языка. <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> Связывает тип содержимого MEF с расширением имени файла, который был зарегистрирован таким образом.  
  
 Чтобы экспортировать определение типа содержимого расширение имени файла, необходимо включить следующие атрибуты:  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: указывает расширение имени файла.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: Указывает тип содержимого.  
  
 Так как <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> запечатанный класс, можно экспортировать его без параметра типа.  
  
 В следующем примере показано атрибутов экспорта расширение имени файла для определения типа содержимого.  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> Управляющая сопоставлениями между расширениями и типы содержимого.  
  
## <a name="extend-classification-types-and-classification-formats"></a>Расширения типов классификации и форматов классификации  
 Типы классификации можно использовать для определения вида текста, для которого вы хотите предоставить различной обработки (например, выделение цветом синий текст «ключевое слово» и «комментарий» зеленый). Определить новый тип классификации путем объявления переменной типа <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> и ей уникальное имя.  
  
 Чтобы зарегистрировать тип классификации с помощью редактора, его нужно экспортируйте вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя типа классификации.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: имя типа классификации, от которого наследует этот тип классификации. Все типы классификации наследовать от «text», и тип классификации может наследовать от нескольких других типов классификации.  
  
 Так как <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> запечатанный класс, можно экспортировать его без параметра типа.  
  
 В следующем примере показано атрибутов экспорта в определении типа классификации.  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> Предоставляет доступ к стандартным классификациям. Встроенные классификации типов относятся следующие:  
  
-   "текст"  
  
-   «естественного языка» (является производным от «text»)  
  
-   (является производным от «text») «формальный язык»  
  
-   «string» (является производным от «literal»)  
  
-   «символ» (является производным от «literal»)  
  
-   «Числовой» (является производным от «literal»)  
  
 Набор ошибок каждого типа наследовать от <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>. К ним относятся следующие типы ошибок:  
  
-   «Синтаксическая ошибка»  
  
-   «Ошибка компилятора»  
  
-   «другие error»  
  
-   «Предупреждение»  
  
 Для получения списка доступных классификации типов, импортировать <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, который поддерживает коллекцию типов классификации для редактора. Следующий код импортирует эту службу как свойство.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 Определение формата классификации можно определить для нового типа классификации. Наследуйте класс от <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> и экспортировать его с типом <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя формата.  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: отображаемое имя формата.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Указывает, отображается ли в формате **шрифты и цвета** странице **параметры** диалоговое окно.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: приоритет формата. Допустимые значения: от <xref:Microsoft.VisualStudio.Text.Classification.Priority>.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: имя классификацию типа, с которым сопоставляется этот формат.  
  
 В следующем примере показано атрибутов экспорта в определении формата классификации.  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 Чтобы получить список доступных форматов, импортируйте <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, который поддерживает коллекцию форматы для редактора. Следующий код импортирует эту службу как свойство.  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## <a name="extend-margins-and-scrollbars"></a>Расширить полей и полос прокрутки  
 Поля и полосы прокрутки — это элементы основное представление редактора Помимо самого представления текста. Вы можете указать любое количество полей, кроме стандартных полей, отображающиеся вокруг представления текста.  
  
 Реализуйте <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> интерфейс для определения полей. Необходимо также реализовать <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> интерфейс для создания поля.  
  
 Чтобы зарегистрировать поставщик margin в редакторе, его необходимо экспортировать поставщика, а также следующие атрибуты:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя поля.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: порядок, в котором отображается поле, относительно других полей.  
  
     Ниже перечислены встроенные поля.  
  
    -   «Полоса прокрутки по горизонтали Wpf»  
  
    -   «Полоса прокрутки по вертикали Wpf»  
  
    -   «Поле номеров строк Wpf»  
  
     Горизонтальная поля, которые имеют атрибут порядка `After="Wpf Horizontal Scrollbar"` отображаются под встроенных полей, а горизонтальная поля, которые имеют атрибут порядка `Before ="Wpf Horizontal Scrollbar"` наверху встроенные поля. Правой кнопкой мыши по вертикали поля, которые имеют атрибут порядка `After="Wpf Vertical Scrollbar"` отображаются справа от полосы прокрутки. Оставить вертикального поля, которые имеют атрибут порядка `After="Wpf Line Number Margin"` отображаются слева от поле с номерами строк (если она видна).  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: тип поля (слева, справа, сверху или снизу).  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, «text» или «code»), для которого действителен в поле.  
  
 В следующем примере показано атрибутов экспорта в поставщике поля для поля, который отображается справа от поле номеров строк.  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extend-tags"></a>Расширить тегов  
 Теги — это способ сопоставления данных с различных видов текста. Во многих случаях связанные данные отображаются в виде визуальный эффект, но не все теги имеют визуального представления. Можно определить собственный тип тега путем реализации <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Необходимо также реализовать <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> для предоставления теги для данного набора текстовых диапазонов и <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> для предоставления средство создания тегов. Необходимо экспортировать поставщика разметчика вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, «text» или «code»), для которого ваши тег является допустимым.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: тип тега.  
  
 В следующем примере показано атрибутов экспорта на поставщика разметчика.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Следующие виды тега являются встроенными:  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: связанные с <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: связанные с типами ошибок.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: сопоставленный элемент оформления.  
  
    > [!NOTE]
    >  Пример <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, см. в разделе Определение HighlightWordTag в [Пошаговое руководство: выделение текста](../extensibility/walkthrough-highlighting-text.md).  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: связанные с регионами, которые можно разворачивать и сворачивать в создания структуры.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: Определяет пространство занимает элемент оформления в представлении текста. Дополнительные сведения о пространства прилежащие элементы оформления в следующем разделе.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: предоставляет автоматические интервалы и определение размера для оформления.  
  
 Поиск и использование тегов для буферы и представления, импортировать <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> или <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, которые предоставляют вам <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> запрошенного типа. Следующий код импортирует эту службу как свойство.  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>Теги и MarkerFormatDefinitions  
 Вы можете расширить <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> класс для определения внешнего вида тега. Необходимо экспортировать классе (как <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя, используемое для ссылки на этот формат  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: это приводит к формат для отображения в пользовательском Интерфейсе  
  
 В конструкторе определить отображаемое имя и внешний вид тега. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> Определяет цвет заливки и <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> определяет цвет границы. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> Локализуемые имя определения формата.  
  
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
  
 Чтобы применить тег данного определения формата, ссылаться на имя, заданные в атрибуте name класса (не отображаемое имя).  
  
> [!NOTE]
>  Пример <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, см. Описание класса HighlightWordFormatDefinition в [Пошаговое руководство: выделение текста](../extensibility/walkthrough-highlighting-text.md).  
  
## <a name="extend-adornments"></a>Расширить элементы оформления  
 Элементы оформления определить визуальные эффекты, которые можно добавить либо к тексту, который отображается в виде текста или к тексту просматривать сам. Можно определить собственные оформления в качестве любого типа <xref:System.Windows.UIElement>.  
  
 В классе оформления, необходимо объявить <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Чтобы зарегистрировать в слое оформлений, его нужно экспортируйте вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя элемента оформления.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: упорядочение, крайнего элемента относительно других слоев оформлений. Класс <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> определяет четыре уровня по умолчанию: выбор, структура, курсор и текст.  
  
 В следующем примере показано атрибутов экспорта в определении слой оформлений.  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 Необходимо создать второй класс, реализующий <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> и обрабатывает его <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> событий путем создания экземпляра оформления. Необходимо экспортировать этот класс, а также следующие атрибуты:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, «text» или «code»), для которого действителен оформления.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: тип представления текста, для которого действителен данным элементом оформления. Класс <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> имеет набор предопределенных ролей представления текста. Например <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> в основном используется для представления текста файлов. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> используется для представления текста, что пользователь может изменить или перемещаться с помощью мыши и клавиатуры. Примеры <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> представления — это представление текстового редактора и **вывода** окна.  
  
 В следующем примере показано атрибутов экспорта на поставщик элемента оформления.  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 Оформления уровня, которое занимает пространство на том же уровне, как текст. Для создания такого рода оформления, необходимо определить класс тег, который наследует от <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, который определяет объем пространства, занимаемого оформления.  
  
 Как и все элементы оформления, его необходимо экспортировать определение слой оформлений.  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 Для создания экземпляра оформления уровня, необходимо создать класс, реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, в дополнение к классу, реализующему <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (как и другие виды элементов оформления).  
  
 Чтобы зарегистрировать поставщика разметчика, его необходимо экспортировать вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, «text» или «code»), для которого действителен вашей оформления.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: тип представления текста, для которого данный тег или оформления является допустимым. Класс <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> имеет набор предопределенных ролей представления текста. Например <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> в основном используется для представления текста файлов. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> используется для представления текста, что пользователь может изменить или перемещаться с помощью мыши и клавиатуры. Примеры <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> представления — это представление текстового редактора и **вывода** окна.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: тип тега или оформления, который вы определили. Необходимо добавить второй <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> для <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.  
  
 В следующем примере показано атрибутов экспорта на поставщике средство создания тегов для тега элемента оформления уровня.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>Расширение мыши процессоров  
 Вы можете добавить специальной обработки ввода от мыши. Создайте класс, наследуемый от <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> и переопределение событий мыши для обработки входных данных. Необходимо также реализовать <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> в второго класса и экспортировать его вместе с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> , указывающий тип содержимого (например, «text» или «code»), для которого действителен Ваш обработчик мыши.  
  
 В следующем примере показано атрибутов экспорта в поставщике процессора мыши.  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extend-drop-handlers"></a>Расширить обработчики перетаскивания  
 Можно настроить поведение обработчики перетаскивания для определенных типов текста, создав класс, реализующий <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> и второй класс, реализующий <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> создать обработчик перетаскивания. Необходимо экспортировать обработчик перетаскивания, а также следующие атрибуты:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: текстовый формат, для которого действителен этот обработчик перетаскивания. Следующие форматы обрабатываются в порядке приоритета от самого высокого до самого низкого:  
  
    1.  Любого пользовательского формата  
  
    2.  FileDrop  
  
    3.  EnhancedMetafile  
  
    4.  WaveAudio  
  
    5.  RIFF  
  
    6.  Dif  
  
    7.  Языковой стандарт  
  
    8.  Палитра  
  
    9. PenData  
  
    10. Сериализуемый  
  
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
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: порядок обработчик перетаскивания до или после обработчика по умолчанию перетаскивания. Обработчик перетаскивания по умолчанию для Visual Studio с именем «DefaultFileDropHandler».  
  
 В следующем примере показано атрибутов экспорта в поставщике обработчик перетаскивания.  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>Расширение параметров редактора  
 Вы можете определить параметры был действителен только в определенной области, например, в представлении текста. Редактор предоставляет этот набор предварительно заданных параметров: параметры редактора, параметры представления и параметров отображения Windows Presentation Foundation (WPF). Эти параметры можно найти в <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, и <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.  
  
 Чтобы добавить новый параметр, следует наследуйте класс от одного из этих классов определение параметра:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 Приведенный ниже показано, как экспортировать определения параметра, который имеет логическое значение.  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extend-intellisense"></a>Расширение IntelliSense  
 IntelliSense — это общий термин для группы компонентов, предоставляющих сведения о структурированного текста и завершение операторов для него. Эти функции включают завершение операторов, Справка по сигнатурам, краткие сведения и лампочки. Завершение операторов помогает пользователям правильно введите ключевое слово или член имя языка. Справка по сигнатурам отображает подпись или подписи для метода, который только что введенное пользователем. Краткие сведения отображается полная сигнатура, имя типа или члена, при наведении указателя мыши на нем. Лампочки предоставляют дополнительные действия для определенных идентификаторов в определенных контекстах, например, переименование все вхождения переменной после переименования одно вхождение.  
  
 Разработка функции IntelliSense — так же, во всех случаях:  
  
-   IntelliSense *broker* отвечает за общий процесс.  
  
-   IntelliSense *сеанса* представляет последовательность событий между вызывающей его срабатывание презентатора и фиксации или отмены выделения. Сеанс инициируется обычно некоторые жест пользователя.  
  
-   IntelliSense *контроллера* отвечает за выбор, когда сеанс должен начала и окончания. Также определяет, когда сведения должны быть зафиксированы и когда следует отменить сеанс.  
  
-   IntelliSense *источника* предоставляет содержимое и определяет наилучшее совпадение.  
  
-   IntelliSense *презентатор* отвечает за отображение содержимого.  
  
 В большинстве случаев рекомендуется ввести по крайней мере источника и контроллера. Если вы хотите настроить отображение можно также предоставить презентатор.  
  
### <a name="implement-an-intellisense-source"></a>Реализация источника IntelliSense  
 Чтобы настроить источник, необходимо реализовать один (или несколько) из следующих интерфейсов источника:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> является устаревшим для <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
 Кроме того необходимо реализовать поставщик того же типа:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> является устаревшим для <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.  
  
 Необходимо экспортировать поставщика, а также следующие атрибуты:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя источника.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, «text» или «code»), к которому относится источник.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: порядок, в которой должен отображаться источника (по отношению к другим источникам).  
  
-   В следующем примере показано атрибутов экспорта в поставщике источника завершения.  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 Дополнительные сведения о реализации источников IntelliSense см. в разделе ниже пошаговых руководства:  
  
 [Пошаговое руководство: Отображение отображение подсказок](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Пошаговое руководство: Отображение справки сигнатуры](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Пошаговое руководство. Отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implement-an-intellisense-controller"></a>Реализуйте контроллер IntelliSense  
 Чтобы настроить контроллер, необходимо реализовать <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> интерфейс. Кроме того необходимо реализовать поставщиком контроллера, а также следующие атрибуты:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя контроллера.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого (например, «text» или «code»), к которому применяется контроллера.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: порядок, в которой должен отображаться контроллера (в отношении других контроллеров).  
  
 В следующем примере показано атрибутов экспорта на поставщик завершений контроллера.  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 Дополнительные сведения об использовании контроллеры IntelliSense см. в разделе ниже пошаговых руководства:  
  
 [Пошаговое руководство: Отображение отображение подсказок](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)