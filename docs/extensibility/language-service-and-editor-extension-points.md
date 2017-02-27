---
title: "Служба языка и точек расширения редактора | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] новый - точек расширения"
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
caps.latest.revision: 33
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 33
---
# Служба языка и точек расширения редактора
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Редактор предоставляет точки расширения, которые можно расширить как части компонента Managed Extensibility Framework \(MEF\), включая большинство функций языковой службы. Ниже приведены категории точки расширения основной:  
  
-   Типы содержимого  
  
-   Классификация типы и форматы классификации  
  
-   Задание полей и полос прокрутки  
  
-   Теги  
  
-   Украшения  
  
-   Мыши процессоров  
  
-   Обработчики перетаскивания  
  
-   Параметры  
  
-   IntelliSense  
  
## Расширение типов содержимого  
 Типы содержимого являются определениями типов текста, обрабатываются с помощью редактора, например, «text», «код» или «C\#». Определить новый тип содержимого, объявив переменную типа <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> и задав новый тип содержимого уникальное имя. Чтобы зарегистрировать тип содержимого с помощью редактора, экспортируйте его вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute> — Имя типа содержимого.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> — Имя типа содержимого, производным которого является данный тип содержимого. Тип содержимого может наследовать из нескольких типов содержимого.  
  
 Поскольку <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> запечатанный класс, вы можете экспортировать без параметра типа.  
  
 В следующем примере показано атрибуты экспорта на определение типа содержимого.  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 Типы содержимого могут основываться на ноль или более существующих типов содержимого. Ниже перечислены встроенные типы:  
  
-   Любое: базовый тип содержимого. Родительский объект для всех типов содержимого.  
  
-   Текст: базовый тип содержимого не проекции. Наследует от «любой».  
  
-   Обычный текст: для текста не кода. Наследует от «text».  
  
-   Код: код всех типов. Наследует от «text».  
  
-   Вставить: исключает текст из любого типа обработки. Этот тип содержимого текста никогда не будет любое расширение, применяемый к нему.  
  
-   Проекция: для содержимое буферов проекции. Наследует от «любой».  
  
-   IntelliSense: для содержимого IntelliSense. Наследует от «text».  
  
-   Sighelp: справка сигнатуры. Наследует от «intellisense».  
  
-   Sighelp\-doc: подпись справочной документации. Наследует от «intellisense».  
  
 Ниже приведены некоторые типы содержимого, которые определены в Visual Studio и некоторые языки, которые размещаются в Visual Studio:  
  
-   Basic  
  
-   C\/C\+\+  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   FindResults  
  
-   F\#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 Для получения списка доступных типов контента, импортировать <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, который поддерживает коллекцию типов содержимого для редактора. Следующий код импортирует эту службу как свойство.  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 Чтобы связать тип содержимого с расширением имени файла, используйте <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>.  
  
> [!NOTE]
>  Расширения имен файлов в Visual Studio, зарегистрированных с помощью <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> на язык пакета службы.<xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> Связывает тип содержимого MEF с расширение имени файла, которое было зарегистрировано таким образом.  
  
 Чтобы экспортировать определение типа содержимого расширение имени файла, необходимо включить следующие атрибуты:  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: задает расширение имени файла.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: задает тип содержимого.  
  
 Поскольку <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> запечатанный класс, вы можете экспортировать без параметра типа.  
  
 В следующем примере показано атрибуты экспорта на расширение имени файла для определения типа содержимого.  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> Управляет ассоциации расширений файлов и типов содержимого.  
  
## Расширение типов классификации и классификацию форматы  
 Классификация типов можно использовать для определения вида текста, для которого вы хотите предоставить различной обработки \(например, выделение цветом зеленый синий текст «ключевое слово» и «комментарий»\). Определите новый тип классификации, объявив переменную типа <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> и выдачу ему уникальное имя.  
  
 Чтобы зарегистрировать тип классификации с помощью редактора, экспортируйте его вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя типа классификации.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: имя типа классификации, от которого наследует этот тип классификации. Все типы классификации наследуют от «text» и тип классификации может наследовать от нескольких других типов классификации.  
  
 Поскольку <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> запечатанный класс, вы можете экспортировать без параметра типа.  
  
 В следующем примере показано атрибуты экспорта в определении типа классификации.  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> Предоставляет доступ к стандартным классификациям. Встроенные классификации типов относятся следующие:  
  
-   "текст"  
  
-   «естественного языка» \(производный от «текст»\)  
  
-   \(производный от «text»\) «формальный язык»  
  
-   «string» \(производный от «literal»\)  
  
-   «символ» \(производный от «literal»\)  
  
-   «Числовой» \(производный от «literal»\)  
  
 Набор ошибок разных типов наследуют от <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>. К ним относятся следующие типы ошибок:  
  
-   «Ошибка синтаксиса»  
  
-   «Ошибка компилятора»  
  
-   «Ошибка других»  
  
-   «Предупреждение»  
  
 Для получения списка доступных типов классификации, импортировать <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, который поддерживает коллекцию типов классификации для редактора. Следующий код импортирует эту службу как свойство.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 Определение формата классификации можно определить для нового типа классификации. Производный класс от <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> и экспортировать его с типом <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>, вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя формата.  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: отображаемое имя формата.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Указывает, отображается ли в формате **шрифты и цвета** страница **Параметры** диалоговое окно.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: приоритет формата. Допустимые значения: от <xref:Microsoft.VisualStudio.Text.Classification.Priority>.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: имя классификации типа, который сопоставлен этот формат.  
  
 В следующем примере показано атрибуты экспорта на определение формата классификации.  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 Для получения списка доступных форматов, импортировать <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, который поддерживает коллекцию форматы для редактора. Следующий код импортирует эту службу как свойство.  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## Расширение полей и полос прокрутки  
 Поля и полосы прокрутки — это элементы основное представление редактора Помимо самого представления текста. Можно указать любое количество полей, кроме стандартных полей, отображаемых вокруг текстового представления.  
  
 Реализуйте <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> интерфейс для определения полей. Необходимо также реализовать <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> интерфейс для создания поля.  
  
 Регистрация поставщика полей с помощью редактора, необходимо экспортировать поставщика вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя поля.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: порядок, в котором отображается поле, относительно других полей.  
  
     Существуют следующие встроенные поля:  
  
    -   «Wpf горизонтальной полосы прокрутки»  
  
    -   «Wpf вертикальной полосы прокрутки»  
  
    -   «Номер поля строки Wpf»  
  
     Горизонтальная полей, имеющих атрибут заказа `After="Wpf Horizontal Scrollbar"` отображаются под встроенные поля, а горизонтальная полей, имеющих атрибут заказа `Before ="Wpf Horizontal Scrollbar"` отображаются над встроенные поля. Правой вертикальной полей, имеющих атрибут заказа `After="Wpf Vertical Scrollbar"` отображаются в правой части полосы прокрутки. Слева вертикальной полей, имеющих атрибут заказа `After="Wpf Line Number Margin"` отображаются в левом поле номеров строк \(если он отображается\).  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: тип поля \(слева, справа, сверху или снизу\).  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого \(например, «text» или «код»\) для которой ваш поля является допустимым.  
  
 В следующем примере показано атрибуты экспорта в поставщике поля для поля справа поле номеров строк.  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## Расширение тегов  
 Теги — это способ связывания данных с различных видов текста. Во многих случаях связанные данные отображаются в виде визуальных эффектов, но не все теги имеют визуального представления. Можно определить собственные типа тегов путем реализации <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Необходимо также реализовать <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> для обеспечения данного набора фрагментов текста, тегов и <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> для обеспечения создания тегов. Необходимо экспортировать создания тегов поставщика вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого \(например, «text» или «код»\) для которой ваш тег является допустимым.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: тип тега.  
  
 В следующем примере показано атрибуты экспорта в поставщике создания тегов.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Встроены следующие виды тега:  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: связанные с <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: связанные с типами ошибок.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: связанные с оформлением.  
  
    > [!NOTE]
    >  Пример <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, см. в определении HighlightWordTag в [Пошаговое руководство: Выделение текста](../extensibility/walkthrough-highlighting-text.md).  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: связанные с областями, которые можно разворачивать и сворачивать в структуры.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: Определяет пространства, занимаемого обрамления в текстовое представление. Дополнительные сведения о крайних элементов уровня в следующем разделе.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: содержит автоматические интервалы и изменения размера для оформления.  
  
 Поиск и использование тегов для буферов и представлений, импортировать <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> или <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, который позволяет <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> запрошенного типа. Следующий код импортирует эту службу как свойство.  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### Теги и MarkerFormatDefinitions  
 Вы можете расширить <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> класса, чтобы определить внешний вид тег. Необходимо экспортировать классе \(как <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>\) со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя, используемое для ссылки на этот формат  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: в результате форматирования для отображения в пользовательском Интерфейсе  
  
 В конструкторе определите отображаемое имя и внешний вид тег.<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> Определяет цвет заливки и <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> определяет цвет границы.<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> Локализуемое имя определения формата.  
  
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
  
 Чтобы применить это определение формата тега, ссылаться на имя, заданные в атрибуте name класса \(не отображаемое имя\).  
  
> [!NOTE]
>  Пример <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, см. класс HighlightWordFormatDefinition в [Пошаговое руководство: Выделение текста](../extensibility/walkthrough-highlighting-text.md).  
  
## Расширение крайних элементов  
 Элементы оформления определяют визуальные эффекты, которые можно добавить любой текст, который отображается в виде текста или к тексту, просмотр сам. Можно определить собственные обрамления как любого типа <xref:System.Windows.UIElement>.  
  
 В классе оформления, необходимо объявить <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Чтобы зарегистрировать уровень обрамления, экспортируйте его вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя элемента оформления.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: упорядочение обрамления по отношению к другим уровням обрамления. Класс <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> определяет четыре уровня по умолчанию: выбор, структурирование, курсор и текст.  
  
 В следующем примере показано атрибуты экспорта в определении уровня обрамления.  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 Необходимо создать второй класс, который реализует <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> и обрабатывает его <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> событий путем создания экземпляра оформления. Необходимо экспортировать этот класс вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого \(например, «text» или «код»\) для которой оформления является допустимым.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: тип представления текста, для которого действителен этот обрамления. Класс <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> имеет набор предопределенных ролей представления текста. Например <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> в основном используется для представления текста из файлов.<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> используется для представления текста, что пользователь может изменить или перемещаться с помощью мыши и клавиатуры. Примеры <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> представления: представление текстового редактора и **вывода** окна.  
  
 В следующем примере показано атрибуты экспорта на поставщике обрамления.  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 Оформления, которое занимает пространство на том же уровне, что и текст. Для создания такого рода оформления, необходимо определить класс тег, который наследует от <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, который определяет объем пространства, занимаемого оформления.  
  
 Как и все элементы оформления, необходимо экспортировать определение слоев обрамления.  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 Чтобы создать оформления уровня, необходимо создать класс, реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, помимо класса, реализующего <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> \(как и другие виды оформления\).  
  
 Чтобы зарегистрировать поставщика создания тегов, его необходимо экспортировать вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого \(например, «text» или «код»\), для которой ваш обрамления является допустимым.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: тип представления текста, для которого данный тег или обрамления является допустимым. Класс <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> имеет набор предопределенных ролей представления текста. Например <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> в основном используется для представления текста из файлов.<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> используется для представления текста, что пользователь может изменить или перемещаться с помощью мыши и клавиатуры. Примеры <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> представления: представление текстового редактора и **вывода** окна.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: тип тега или оформления, который был определен. Необходимо добавить второй <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> для <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.  
  
 В следующем примере показано атрибуты экспорта поставщика создания тегов для тега уровня обрамления.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## Расширение мыши процессоров  
 Можно добавить специальной обработки ввода от мыши. Создайте класс, наследуемый от <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> и переопределение событий мыши для ввода, необходимо обработать. Необходимо также реализовать <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> в второго класса и экспортировать его вместе с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> указывает тип содержимого \(например, «text» или «код»\), для которого действителен обработчик мыши.  
  
 В следующем примере показано атрибуты экспорта в поставщике мыши процессора.  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## Расширение обработчики перетаскивания  
 Можно настроить поведение обработчики перетаскивания для определенных типов текста, создав класс, реализующий <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> и второй класс, который реализует <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> создать обработчик перетаскивания. Необходимо экспортировать обработчик перетаскивания, а также следующие атрибуты:  
  
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
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: упорядочение обработчик перетаскивания до или после удаления обработчика по умолчанию. По умолчанию обработчик перетаскивания для Visual Studio называется «DefaultFileDropHandler».  
  
 В следующем примере показано атрибуты экспорта в поставщике обработчик перетаскивания.  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## Расширение параметров редактора  
 Можно определить параметры действовали только в определенной области, например, в виде текста. Редактор предоставляет этот набор стандартных параметров: параметры редактора, просмотрите параметры и параметры просмотра Windows Presentation Foundation \(WPF\). Эти параметры можно найти в <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, и <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.  
  
 Чтобы добавить новый параметр, создать класс, производный от одного из этих классов определение параметров:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 В следующем примере показано, как для экспорта определения параметра, который имеет логическое значение.  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## Расширение IntelliSense  
 IntelliSense — это общий термин для нескольких компонентов, предоставляющих сведения о структурированных текстовых и завершение операторов для него. Эти функции включают завершение операторов, справка сигнатуры, кратких сведений и лампочки. Завершение операторов помогает пользователям правильно введите ключевое слово или члена имя языка. Справка сигнатуры отображает подпись или подписи для метода, который только что введенное пользователем. Краткие сведения отображает полную подпись, имя типа или члена, при наведении указателя мыши на его. Лампочки предоставляют дополнительных действий для определенных идентификаторов в определенных контекстах, например, переименование всех вхождений переменной после переименования один раз.  
  
 Разработано функцию IntelliSense точно так же, во всех случаях:  
  
-   IntelliSense *broker* отвечает за процесс в целом.  
  
-   IntelliSense *сеанса* представляет последовательность событий между выполняемой презентатора и фиксации или отмены выделения. Некоторые жест пользователя обычно запускается сеанс.  
  
-   IntelliSense *контроллера* отвечает за определение, когда должно начинаться и заканчиваться сеанса. Также решает, когда информация может быть зафиксирована и когда сеанса должны быть отменены.  
  
-   IntelliSense *источника* предоставляет содержимое и решает наилучшего соответствия.  
  
-   IntelliSense *презентатор* отвечает за отображение содержимого.  
  
 В большинстве случаев рекомендуется ввести по крайней мере источника и контроллера. Также можно предоставить презентатор, если вы хотите настроить отображение.  
  
### Реализация источника IntelliSense  
 Чтобы настроить источник, необходимо реализовать один \(или более\) из следующих интерфейсов источника:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> является устаревшим для <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
 Кроме того необходимо реализовать поставщик одного типа:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> является устаревшим для <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.  
  
 Необходимо экспортировать поставщика вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя источника.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого \(например, «text» или «код»\) к которому применяется источника.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: порядок источник должен \(относительно других источников\).  
  
-   В следующем примере показано атрибуты экспорта в поставщике источника завершения.  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 Дополнительные сведения о реализации источников IntelliSense см. следующие примеры:  
  
 [Пошаговое руководство: Отображение кратких сведений подсказки](../Topic/Walkthrough:%20Displaying%20QuickInfo%20Tooltips.md)  
  
 [Пошаговое руководство: Отображение справки сигнатуры](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Пошаговое руководство: Отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### Реализация контроллер IntelliSense  
 Чтобы настроить контроллер, необходимо реализовать <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> интерфейса. Кроме того необходимо реализовать поставщик controller вместе со следующими атрибутами:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя контроллера.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: тип содержимого \(например, «text» или «код»\) к которому применяется контроллером.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: заказа, в которых должен отображаться контроллер \(по отношению к контроллерам\).  
  
 В следующем примере показано атрибуты экспорта в поставщике контроллера завершения.  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 Дополнительные сведения об использовании IntelliSense контроллеров см. следующие примеры:  
  
 [Пошаговое руководство: Отображение кратких сведений подсказки](../Topic/Walkthrough:%20Displaying%20QuickInfo%20Tooltips.md)