---
title: Языковая служба и баллы расширения редактора Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28bb086eb99e4b8128c04f62f9b370eb2eab8fa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703056"
---
# <a name="language-service-and-editor-extension-points"></a>Языковой сервис и точки расширения редактора
Редактор предоставляет точки расширения, которые можно расширить в качестве компонентов управляемой рамки расширения (MEF), включая большинство функций языковой службы. Вот основные категории пунктов расширения:

- Типы содержимого

- Типы классификации и форматы классификации

- Поля и прокрутки

- Теги

- Украшения

- Мышиные процессоры

- Обработчики выпадения

- Параметры

- IntelliSense

## <a name="extend-content-types"></a>Расширение типов содержимого
 Типы содержимого — это определения видов текста, обрабатываемых редактором, например, "текст", "код" или "CSharp". Вы определяете новый тип содержимого, <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> объявляя переменную типа и придавая новому типу содержимого уникальное имя. Чтобы зарегистрировать тип содержимого в редакторе, экспортируйте его вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>— это название типа содержимого.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>— это название типа содержимого, из которого происходит этот тип содержимого. Тип содержимого может наследоваться из нескольких других типов содержимого.

  Поскольку <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> класс опечатан, его можно экспортировать без параметра типа.

  В следующем примере показаны атрибуты экспорта в определении типа содержимого.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 Типы содержимого могут основываться на нулевых или более уже существующих типах содержимого. Это встроенные типы:

- Любой: базовый тип содержимого. Родитель всех других типов контента.

- Текст: базовый тип для непроекционного контента. Наследует от "любого".

- Plaintext: для некодового текста. Наследует от "текста".

- Код: для кода всех видов. Наследует от "текста".

- Инертный: исключает текст из любого вида обработки. Текст этого типа содержимого никогда не будет применяться к нему.

- Проекция: для содержимого проекционных буферов. Наследует от "любого".

- Intellisense: для содержания IntelliSense. Наследует от "текста".

- Sighelp: подпись помочь. Наследует от "интеллект".

- Sighelp-doc: документация справки подписи. Наследует от "интеллект".

  Вот некоторые из типов контента, которые определяются Visual Studio, и некоторые языки, размещенные в Visual Studio:

- Basic

- C/C++

- Консольный выход

- C#

- CSS

- Enc

- НайтиРезультаты

- F#

- HTML

- Язык JScript

- XAML

- XML

  Чтобы обнаружить список доступных <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>типов контента, импортируйте , который поддерживает сбор типов контента для редактора. Следующий код импортирует эту услугу как свойство.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Чтобы связать тип содержимого с расширением имени файла, используйте: <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>

> [!NOTE]
> В Visual Studio расширения имен файлов регистрируются с помощью <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> пакета языковых услуг. Ассоциирует <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> тип содержимого MEF с расширением имени файла, которое было зарегистрировано таким образом.

 Чтобы экспортировать расширение имени файла в определение типа содержимого, необходимо включить следующие атрибуты:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: определяет расширение имени файла.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: определяет тип содержимого.

  Поскольку <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> класс опечатан, его можно экспортировать без параметра типа.

  В следующем примере показаны атрибуты экспорта в расширении имени файла к определению типа содержимого.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 Управление <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> ассоциациями между расширениями имен файлов и типами содержимого.

## <a name="extend-classification-types-and-classification-formats"></a>Расширение типов классификации и форматов классификации
 Типы классификации можно использовать для определения видов текста, для которых требуется различная обработка (например, раскраска текста "ключевое слово" синим и "комментарий" текст зеленый). Определите новый тип классификации, <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> объявив переменную типа и придав ему уникальное имя.

 Чтобы зарегистрировать тип классификации с редактором, выведите его вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: название типа классификации.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: название типа классификации, из которого этот тип классификации наследует. Все типы классификации наследуются от "текста", а тип классификации может наследовать сяочку из нескольких других типов классификации.

  Поскольку <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> класс опечатан, его можно экспортировать без параметра типа.

  В следующем примере показаны атрибуты экспорта в определении типа классификации.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 Обеспечивает <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> доступ к стандартным классификациям. Встроенные типы классификации включают в себя следующие:

- "text"

- "естественный язык" (вывод из "текста")

- "формальный язык" (выводизется из "текста")

- "строка" (производные от "буквального")

- "характер" (производные от "буквального")

- "числовая" (производные от "буквального")

  Набор различных типов ошибок наследуют от <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>. Они включают в себя следующие типы ошибок:

- "ошибка синтаксиса"

- "Ошибка компилятора"

- "другая ошибка"

- "предупреждение"

  Чтобы обнаружить список доступных <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>типов классификации, импортируйте , который поддерживает сбор типов классификации для редактора. Следующий код импортирует эту услугу как свойство.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Можно определить определение формата классификации для нового типа классификации. Выизведите <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> класс и экспортите его с типом, <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: название формата.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: название дисплея формата.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: определяет, отображается ли формат на странице **шрифтов и цветов** диалогового окна **Options.**

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: приоритет формата. Допустимые значения <xref:Microsoft.VisualStudio.Text.Classification.Priority>от .

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: название типа классификации, к которому отображается этот формат.

  В следующем примере показаны атрибуты экспорта в определении формата классификации.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 Чтобы открыть для себя список <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>доступных форматов, импортируйте, который поддерживает коллекцию форматов для редактора. Следующий код импортирует эту услугу как свойство.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Расширить поля и прокрутки
 Поля и прокрутки являются основными элементами представления редактора в дополнение к самому текстовому представлению. Вы можете предоставить любое количество полей в дополнение к стандартным полям, которые отображаются вокруг представления текста.

 Реализация <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> интерфейса для определения маржи. Необходимо также реализовать <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> интерфейс для создания поля.

 Чтобы зарегистрировать поставщика маржи с редактором, необходимо экспортировать поставщика вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: название поля.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: порядок, в котором маржа появляется, по сравнению с другими полями.

   Это встроенные поля:

  - "Wpf Горизонтальный Прокрутка"

  - "Вертикальная прокрутка Wpf"

  - "Wpf Линия номер маржи"

    Горизонтальные поля, которые имеют `After="Wpf Horizontal Scrollbar"` атрибут заказа, отображаются ниже встроенной поляны, а горизонтальные поля, которые имеют атрибут заказа, `Before ="Wpf Horizontal Scrollbar"` отображаются выше встроенной поляны. Правые вертикальные поля, которые `After="Wpf Vertical Scrollbar"` имеют атрибут заказа, отображаются справа от панели прокрутки. Левые вертикальные края, которые `After="Wpf Line Number Margin"` имеют атрибут заказа, появляются слева от поля номера линии (если она видна).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: вид поля (левый, правый, верхний или нижний).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: вид контента (например, "текст" или "код"), для которого ваша маржа действительна.

  В следующем примере показаны экспортные атрибуты на марже поставщика для маржи, которая кажется справа от маржи числа строк.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Расширить теги
 Теги — это способ связывания данных с различными видами текста. Во многих случаях связанные данные отображаются как визуальный эффект, но не все теги имеют визуальную презентацию. Вы можете определить свой собственный <xref:Microsoft.VisualStudio.Text.Tagging.ITag>вид тега, реализовав. Необходимо также <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> реализовать, чтобы предоставить теги для заданного <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> набора текстовых диапазонов, а также предоставить теггер. Вы должны экспортировать поставщика tagger вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: вид содержимого (например, "текст" или "код"), для которого ваш тег действителен.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: вид тега.

  В следующем примере показаны атрибуты экспорта на поставщике tagger.

\<CodeContentPlaceHolder></CodeContentPlaceHolder> 8 Следующие виды тегов встроены:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: связанный <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>с .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: связанные с типами ошибок.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: связанс с украшением.

  > [!NOTE]
  > Для примера <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, см. определение HighlightWordTag в [Пошагово: Выделение текста](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: связанные с регионами, которые могут быть расширены или рухнули в изложении.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: определяет пространство, занимаемое украшением в текстовом представлении. Для получения дополнительной информации об украшениях для переговоров о космосе см.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: обеспечивает автоматическое расстояние и размер для украшения.

  Чтобы найти и использовать теги для буферов и представлений, импортируйте <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> или <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, которые дают вам запрашиваемый <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> тип. Следующий код импортирует эту услугу как свойство.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Теги и маркерФорматныеОпределения
 Можно расширить <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> класс, чтобы определить внешний вид тега. Вы должны экспортировать свой <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>класс (как) со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя, используемое для ссылки на этот формат

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: это приводит к тому, что формат появляется в uI

  В конструкторе определяется имя дисплея и внешний вид тега. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A>определяет цвет заполнения и <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> определяет цвет границы. Это <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> локальное название определения формата.

  Ниже приводится пример определения формата:

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

 Чтобы применить это определение формата к тегу, отобрадайте имя, установленное в атрибуте имени класса (а не имя дисплея).

> [!NOTE]
> Для примера <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, см. выделитеWordFormatОпределение класса в [Пошаговая: Выделение текста](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Продлить украшения
 Украшения определяют визуальные эффекты, которые могут быть добавлены либо к тексту, который отображается в текстовом представлении, либо к самому текстовому представлению. Вы можете определить свой собственный <xref:System.Windows.UIElement>украшение, как любой тип .

 В вашем классе украшений, <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>вы должны объявить . Чтобы зарегистрировать слой украшения, вывешив его вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: название украшения.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: заказ украшения по отношению к другим слоям украшения. Класс <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> определяет четыре слоя по умолчанию: выбор, выделение, Caret и Текст.

  В следующем примере показаны атрибуты экспорта в определении слоя украшения.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 Необходимо создать второй класс, <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> который реализует <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> и обрабатывает свое событие, мгновенно украшая. Вы должны экспортировать этот класс вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: вид содержимого (например, "текст" или "код"), для которого украшение является действительным.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: вид представления текста, для которого это украшение является действительным. Класс <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> имеет набор предопределенных ролей представления текста. Например, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> в основном используется для текстовых представлений файлов. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>используется для текстовых представлений, которые пользователь может отсеить или перемещать с помощью мыши и клавиатуры. Примерами <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> представлений являются текстовый вид редактора и окно **вывода.**

  В следующем примере показаны экспортные атрибуты поставщика украшений.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Украшение, переговорное в пространстве, занимает пространство на том же уровне, что и текст. Чтобы создать такого рода украшения, необходимо определить класс <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>тегов, который наследует от , который определяет количество места, занимаемое украшением.

 Как и во всех украшениях, вы должны экспортировать определение слоя украшения.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Чтобы мгновенно украсить пространство-переговоры, вы должны создать <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>класс, который реализует, <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> в дополнение к классу, который реализует (как и другие виды украшений).

 Чтобы зарегистрировать поставщика tagger, вы должны экспортировать его вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: вид контента (например, "текст" или "код"), для которого ваше украшение является действительным.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: вид представления текста, для которого этот тег или украшение является действительным. Класс <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> имеет набор предопределенных ролей представления текста. Например, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> в основном используется для текстовых представлений файлов. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>используется для текстовых представлений, которые пользователь может отсеить или перемещать с помощью мыши и клавиатуры. Примерами <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> представлений являются текстовый вид редактора и окно **вывода.**

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: вид тега или украшения, которые вы определили. Вы должны добавить секунду <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> для <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.

  В следующем примере отображаются атрибуты экспорта на поставщике tagger для тега украшения для космических переговоров.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Расширение процессоров мыши
 Можно добавить специальную обработку для ввода мыши. Создайте класс, который <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> наследует и переопределить события мыши для ввода, который вы хотите обрабатывать. Необходимо также <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> реализовать во втором классе и <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> экспортировать его вместе с тем, который определяет вид содержимого (например, "текст" или "код"), для которого обработчик мыши действителен.

 В следующем примере показаны экспортные атрибуты поставщика процессоров мыши.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Расширить обработчики сбросов
 Можно настроить поведение обработчиков капель для определенных видов текста, <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> создав класс, <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> который реализует, и второй класс, который реализует для создания обработчика капель. Вы должны экспортировать обработчик капли вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: текстовый формат, для которого этот обработчик капли действителен. Следующие форматы обрабатываются в порядке приоритета от самого высокого до самого низкого:

  1. Любой пользовательский формат

  2. FileDrop

  3. Улучшенныйметафил

  4. WaveAudio

  5. Riff

  6. Dif

  7. Локаль

  8. Палитра

  9. PenData

  10. Упорядочиваемый уровень изоляции

  11. Символическаяссылка

  12. Xaml

  13. XamlPackage

  14. Tiff

  15. Bitmap

  16. Dib

  17. MetafilePicture

  18. CSV

  19. System.String

  20. Html Формат

  21. UnicodeText

  22. OEMText

  23. Text

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя обработчика капли.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: заказ обработчика капли до или после обработчика капли по умолчанию. Обработчик падения по умолчанию для Visual Studio называется "DefaultFileDropHandler".

  В следующем примере показаны атрибуты экспорта в поставщике обработчиков капель.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Расширение вариантов редактора
 Параметры можно определить, чтобы они были действительны только в определенной области, например, в текстовом представлении. Редактор предоставляет этот набор предопределенных вариантов: параметры редактора, параметры просмотра и параметры представления Windows Presentation Foundation (WPF). Эти варианты можно <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>найти <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>в , и .

 Чтобы добавить новую опцию, вывемите класс из одного из этих классов определения вариантов:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  Ниже приводится следующий пример, как экспортировать определение опциона, который имеет значение Boolean.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Расширить IntelliSense
 IntelliSense — это общий термин для группы функций, предоставляющих информацию о структурированном тексте и завершении заявления для него. Эти функции включают в себя завершение оператора, помощь в подписи, Быстрая информация и лампочки. Завершение выполнения заявления помогает пользователям правильно введите ключевое слово или имя пользователя. Подпись помогает отображать подпись или подписи для метода, который пользователь только что набрал. Быстрая информация отображает полную подпись для типа или имени члена, когда мышь опирается на него. Лампочка предоставляет дополнительные действия для определенных идентификаторов в определенных контекстах, например, переименование всех случаев переменной после того, как одно явление было переименовано.

 Дизайн функции IntelliSense во всех случаях одинаков:

- Брокер IntelliSense *broker* отвечает за общий процесс.

- *Сеанс* IntelliSense представляет последовательность событий между запуском докладчика и коммитталом или отменой выбора. Сеанс обычно запускается каким-то жестом пользователя.

- *Контроллер* IntelliSense отвечает за принятие решения о том, когда сеанс должен начаться и закончиться. Он также принимает решение о том, когда информация должна быть совершена и когда сессия должна быть отменена.

- *Источник* IntelliSense предоставляет содержимое и определяет наилучший матч.

- *Ведущий* IntelliSense отвечает за отображение содержимого.

  В большинстве случаев мы рекомендуем предоставить хотя бы источник и контроллер. Вы также можете предоставить докладчика, если вы хотите настроить дисплей.

### <a name="implement-an-intellisense-source"></a>Реализация источника IntelliSense
 Чтобы настроить исходный чеисточник, необходимо реализовать один (или более) из следующих интерфейсов исходного кода:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource>был уволен в пользу <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.

 Кроме того, необходимо реализовать поставщика того же вида:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider>был уволен в пользу <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.

 Вы должны экспортировать поставщика вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя источника.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: вид содержимого (например, "текст" или "код"), к которому применяется источник.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: порядок, в котором должен отображаться источник (по отношению к другим источникам).

- В следующем примере показаны атрибуты экспорта в поставщике источников завершения.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 Для получения дополнительной информации о реализации источников IntelliSense, см.

- [Прохождение: Отображение инструментов quickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Пошаговая прогулка: Помощь в отображении подписи](../extensibility/walkthrough-displaying-signature-help.md)

- [Пошаговое руководство. Отображение завершения операторов](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Реализация контроллера IntelliSense
 Чтобы настроить контроллер, необходимо реализовать <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> интерфейс. Кроме того, необходимо реализовать поставщика контроллеров вместе со следующими атрибутами:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: имя контроллера.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: вид содержимого (например, "текст" или "код"), к которому применяется контроллер.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: порядок, в котором должен отображаться контроллер (по отношению к другим контроллерам).

  В следующем примере показаны экспортные атрибуты поставщика контроллеров завершения.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 Для получения дополнительной информации об использовании контроллеров IntelliSense см.

- [Прохождение: Отображение инструментов quickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
