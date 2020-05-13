---
title: Шрифты и форматирование для визуальной студии Документы Майкрософт
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf1550026fb5c9d9395d931f21d48bc4739ea8c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698580"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Шрифты и форматирование для Visual Studio
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a>Шрифт среды
 Все шрифты в Visual Studio должны быть выставлены пользователю для настройки. В первую очередь это делается через страницу **шрифтов и цветов** в диалоге **«Инструменты > варианты».** Три основные категории настроек шрифта:

- **Шрифт среды** - основной шрифт для IDE (интегрированная среда разработки), используемый для всех элементов интерфейса, включая диалоги, меню, окна инструментов и окна документов. По умолчанию шрифт среды привязан к системному шрифту, который отображается как 9 pt Segoe UI в текущих версиях Windows. Использование одного шрифта для всех элементов интерфейса помогает обеспечить согласованный внешний вид шрифта на протяжении всей IDE.

- **Текстовый редактор** - элементы, которые посевные в коде и других текстовых редакторов могут быть настроены на странице текстредактора в **Инструменты > варианты**.

- **Конкретные коллекции** - дизайнерские окна, которые предлагают пользовательские настройки элементов интерфейса, могут подвергать шрифты, характерные для их поверхности дизайна, в их собственной странице настроек в **Tools > Options.**

### <a name="editor-font-customization-and-resizing"></a>Настройка шрифта редактора и изменения размера
 Пользователи часто увеличивают или увеличивают размер и/или цвет текста в редакторе в зависимости от их предпочтений, независимо от общего пользовательского интерфейса. Поскольку шрифт среды используется на элементах, которые могут появиться в элементах или в составе редактора/дизайнера, важно отметить ожидаемое поведение при изменении одной из этих классификаций шрифтов.

 При создании элементов uI, которые отображаются в редакторе, но не являются частью *содержимого,* важно использовать шрифт среды, а не текстовый шрифт, чтобы элементы изменялись предсказуемым образом.

1. Для текста кода в редакторе, изменить размер с настройкой текста кода и ответить на уровень масштабирования текста редактора.

2. Все остальные элементы интерфейса должны быть привязаны к настройке шрифта среды и реагировать на любые глобальные изменения в среде. Это включает в себя (но не ограничивается):

    - Текст в контекстных меню

    - Текст в редакции украшения, как лампочка меню текста, быстро найти панель редактора, и перемещаться в панель

    - Текст этикетки в диалоговых коробках, **например, Найти в файлах** или **рефактор**

### <a name="accessing-the-environment-font"></a>Доступ к шрифту среды
 В коде Native или WinForms можно получить доступ `IUIHostLocale::GetDialogFont` к шрифту среды, `SID_SUIHostLocale` позвонив по методу после запроса интерфейса службы.

 Для Фонда презентации Windows (WPF) вычеркните `DialogWindow` класс окна диалога `Window` из класса оболочки вместо класса WPF.

 В XAML код выглядит следующим образом:

```xaml
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>
```

Код позади:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 (Заменить `Microsoft.VisualStudio.Shell.11.0` текущую версию MPF dll.)

 Чтобы отобразить диалог, позвоните`ShowModal()` `ShowDialog()`" на класс более . `ShowModal()`устанавливает правильное состояние модального состояния в оболочке, обеспечивает центр и среду диалог в родительском окне и так далее.

 Код заключается в следующем:

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal`возвращает бул? (недействительный Boolean) `DialogResult`с , которые могут быть использованы в случае необходимости. Значение возврата верно, если диалог был закрыт с **OK**.

 Если вам нужно отобразить некоторый UI WPF, который `HwndSource`не является диалогом и размещается в своем собственном, например, всплывающее окно `FontFamily` или `FontSize` окно ребенка WPF родительского окна Win32/WinForms, вам нужно будет установить и на корневой элемент элемента WPF. (Оболочка устанавливает свойства на главном окне, но они `HWND`не будут унаследованы мимо). Оболочка предоставляет ресурсы, к которым свойства могут быть связаны, как это:

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a>Ссылка на форматирование (масштабирование/смазывание)
 Некоторые диалоги требуют, чтобы определенный текст был смелым или размером, кроме шрифта среды. Ранее шрифты, превышающее шрифт среды, кодировались как «подобные`environment font +2`или аналогичные. Использование предоставленных фрагментов кода будет поддерживать мониторы с высоким dPI и гарантировать, что текст отображения всегда отображается в нужном размере и весе (например, Light или Semilight).

> [!NOTE]
> Перед тем, как применить форматирование, убедитесь, что вы следуете указаниям, найденным в [стиле Text».](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

 Для масштабирования шрифта среды установите стиль TextBlock или Label в указании. Каждый из этих фрагментов кода, правильно используемых, будет генерировать правильный шрифт, в том числе соответствующие изменения размера и веса.

 Где`vsui`" является отсылкой к области `Microsoft.VisualStudio.Shell`имен :

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>375% Окружающая среда шрифта

**Появляется как:** 34 pt Segoe UI Light

::: moniker range="vs-2017"

**Использование для:** (редко) уникальный фирменный uI, как в стартовой странице

::: moniker-end

::: moniker range=">=vs-2019"

**Использование для:** (редко) уникальный фирменный uI

::: moniker-end

**Процедурный код:** Где `textBlock` находится ранее определенный `label` TextBlock и является ранее определенной этикеткой:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** Установите стиль TextBlock или Label в виде показаний.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>310% Окружающая среда шрифта
 **Появляется как:** 28 pt Segoe UI Light **Use для:** большие названия диалога подписи, основной заголовок в отчетах

 **Процедурный код:** Где `textBlock` находится ранее определенный `label` TextBlock и является ранее определенной этикеткой:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** Установите стиль TextBlock или Label в виде показаний.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>200% Окружающая среда шрифта
 **Появляется как:** 18 pt Segoe UI Полусвет **Использование для:** подзаголовки, названия в малых и средних диалогов

 **Процедурный код:** Где `textBlock` находится ранее определенный `label` TextBlock и является ранее определенной этикеткой:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** Установите стиль TextBlock или Label в показано:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>155% Шрифт окружающей среды
 **Появляется как:** 14 pt Segoe UI **Использование для:** раздел заголовки в документе хорошо UI или отчеты

 **Процедурный код:** Где `textBlock` находится ранее определенный `label` TextBlock и является ранее определенной этикеткой:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** Установите стиль TextBlock или Label в показано:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>133% Шрифт окружающей среды
 **Появляется как:** 12 pt Segoe UI **Использование для:** меньшие подзаголовки в подписных диалогов и документ хорошо UI

 **Процедурный код:** Где `textBlock` находится ранее определенный `label` TextBlock и является ранее определенной этикеткой:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** Установите стиль TextBlock или Label в показано:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>122% Окружающая среда шрифт
 **Появляется как:** 11 pt Segoe UI **Использование для:** раздел заголовки в подписи диалогов, верхние узлы в виде дерева, вертикальная навигация вкладки

 **Процедурный код:** Где `textBlock` находится ранее определенный `label` TextBlock и является ранее определенной этикеткой:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** Установите стиль TextBlock или Label в показано:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>Шрифт окружающей среды и жирный
 **Появляется как:** смелый 9 pt Segoe UI **Использование для:** этикетки и подголовы в подписи диалогов, отчетов и документ хорошо UI

 **Процедурный код:** Где `textBlock` находится ранее определенный `label` TextBlock и является ранее определенной этикеткой:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** Установите стиль TextBlock или Label в показано:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>Локализованные стили
 В некоторых случаях локализаторам необходимо будет модифицировать стили шрифтов для различных языков, например, удаление смелых из текста для восточноазиатских языков. Чтобы сделать локализацию стилей шрифтов возможной, эти стили должны быть в файле .resx. Лучший способ достичь этого и до сих пор редактом стилей шрифтов в Visual Studio формы дизайнера явно установить шрифт стилей во время проектирования. Хотя это создает объект полного шрифта и может показаться, что нарушает наследование родительских шрифтов, только свойство FontStyle используется для установки шрифта.

 Решение состоит в том, чтобы `FontChanged` зацепить событие формы диалога. В `FontChanged` этом случае, ходить все элементы управления и проверить, если их шрифт установлен. Если он установлен, измените его на новый шрифт на основе шрифта формы и предыдущего стиля шрифта управления. Примером этого в коде является:

```csharp
private void Form1_FontChanged(object sender, System.EventArgs e)
{
          SetFontStyles();
}

/// <summary>
/// SetFontStyles - This function will iterate all controls on a page
/// and recreate their font with the desired fontstyle.
/// It should be called in the OnFontChanged handler (and also in the constructor
/// in case the IUIService is not available so OnFontChange doesn't fire).
/// This way, when the VS shell font is given to us the controls that have
/// a different style for the font (bolded for example) will recreate their font
/// and use the VS shell font but with a style variation (bolded ...).
/// </summary>
protected void SetFontStyles()
{
     SetFontStyles(this, this, this.Font);
}

protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)
{
     foreach(Control c in parent.Controls)
     {
          if (c.Controls != null && c.Controls.Count > 0) {
               SetFontStyles(topControl, c, referenceFont);
          }
          if (c.Font != topControl.Font) {
               c.Font = new Font(referenceFont, c.Font.Style);
          }
     }
}
```

 Использование этого кода гарантирует, что при обновлении шрифта формы также будут обновляться шрифты элементов управления. Этот метод также следует вызывать из конструктора формы, потому что диалог `IUIService` может `FontChanged` не получить экземпляр и событие никогда не будет гореть. Подключение `FontChanged` позволит диалогов динамически подобрать новый шрифт, даже если диалог уже открыт.

### <a name="testing-the-environment-font"></a>Тестирование шрифта среды
 Чтобы убедиться, что ваш шрифт использования среды и уважает параметры размера, откройте **инструменты > варианты > среды > шрифты и цвета** и выберите "Экологический шрифт" в "Показать настройки для:" выпадающие меню.

 ![Настройки шрифтов и цветов &gt; в диалоге опций «Инструменты»](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />Настройки шрифтов и цветов &gt; в диалоге опций «Инструменты»

 Установите шрифт на что-то очень различное, чем по умолчанию. Чтобы было очевидно, какой uI не обновляется, выберите шрифт с засечками (например, "Times New Roman") и установите очень большой размер. Затем проверьте свой uI, чтобы убедиться, что он уважает окружающую среду. Вот пример с помощью лицензионного диалога:

 ![Пример текста uI, который не уважает шрифт окружающей среды](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />Пример текста uI, который не уважает шрифт окружающей среды

 В этом случае "Информация пользователя" и "Информация о продуктах" не соблюдают шрифт. В некоторых случаях это может быть явным выбором дизайна, но это может быть ошибка, если явный шрифт не указан как часть спецификаций redline.

 Чтобы сбросить шрифт, нажмите "Использовать по умолчанию" под **инструментом > опций > среда > шрифты и цвета.**

## <a name="text-style"></a><a name="BKMK_TextStyle"></a>Текстовый стиль
 Текстовый стиль относится к размеру шрифта, весу и корпусу. Для руководства по реализации [см.](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)

### <a name="text-casing"></a>Текстовый корпус

#### <a name="all-caps"></a>Все прописные
 Не используйте все колпачки для заголовков или этикеток в Visual Studio.

#### <a name="all-lowercase"></a>Все нижние регистры
 Не используйте все нижние регистры для названий или этикеток в Visual Studio.

#### <a name="sentence-and-title-case"></a>Приговор и название дела
 Текст в Visual Studio должен использовать либо название случае или приговор случае, в зависимости от ситуации.

|Используйте титульный кейс для:|Используйте приговор случае для:|
|-------------------------|----------------------------|
|Названия диалогов|Метки|
|Групповые ящики|Флажки|
|Пункты меню|Переключатели|
|Элементы контекстного меню|Список элементов коробки|
|Кнопки|Строки состояния|
|Наклейки на стол||
|Заголовки столбцов||
|Всплывающие подсказки||

##### <a name="title-case"></a>Заглавные буквы
 Название случае стиль, в котором первые буквы большинства или всех слов в фразе капитализируются. В Visual Studio, название случае используется для многих элементов, в том числе:

- **Подсказки.** Пример: "Предварительный просмотр выбранных элементов"

- **Заголовки столбцов.** Пример: "Системный ответ"

- **Пункты меню.** Пример: "Спасти всех"

  При использовании титульного кейса, эти руководящие принципы, когда капитализировать слова и когда оставить их нижнего регистра:

|Верхний регистр|Комментарии и примеры|
|---------------|---------------------------|
|Все существить||
|Все глаголы|В том числе "Is" и другие формы "быть"|
|Все наречия|В том числе "Тан" и "Когда"|
|Все прилагательные|В том числе "Это" и "Это"|
|Все хвоисты|В том числе притяжательные "Its", а также "Это", сокращение стояк "это" и глагол "есть"|
|Первые и последние слова, независимо от частей речи||
|Предлоги, которые являются частью глагослова|"Закрытие всех Windows" или "Закрытие системы"|
|Все буквы аббревиатуры|HTML, XML, URL, IDE, RGB|
|Второе слово в сложном слове, если это существительное или правильное прилагательное, или если слова имеют равный вес|Перекрестная ссылка, программное обеспечение pre-Microsoft, Доступ к чтению/записи, время выполнения|

|Нижний регистр|Примеры|
|---------------|--------------|
|Второе слово в сложном слове, если это другая часть речи или участие изменения первого слова|Как-к, Взлет|
|Статьи, если одно не первое слово в названии|a, an, the|
|Координация соединений|и, но, для, ни, или|
|Предлоги со словами из четырех или менее букв за пределами глагольной фразы|в, на, как для, из, на вершине|
|"К" при использовании в бесконечной фразе|"Как форматировать ваш жесткий диск"|

##### <a name="sentence-case"></a>Приговор случае
 Приговор случае является стандартным методом капитализации для написания, в котором только первое слово предложения капитализируются, наряду с любыми надлежащими существительными и местоимение "Я". В общем случае предложения легче читать мировой аудитории, особенно когда контент будет переведен машиной. Используйте приговор случае для:

1. **Сообщения о статус-барах.** Они просты, короткие, и предоставляют только информацию о состоянии. Пример: "Загрузка файла проекта"

2. **Все остальные элементы uI,** включая метки, флажки, радиокнопки и элементы списка коробок. Пример: "Выберите все элементы в списке"

### <a name="text-formatting"></a>Форматирование текста
 Формат текста по умолчанию в Visual Studio 2013 контролируется [шрифтом «Окружающая среда».](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont) Эта услуга помогает обеспечить согласованный внешний вид шрифта во всей IDE (интегрированная среда разработки), и вы должны использовать его, чтобы гарантировать согласованный опыт для ваших пользователей.

 Размер по умолчанию, используемый службой шрифтов Visual Studio, поступает из Windows и отображается как 9 pt.

 Можно применить форматирование к шрифту среды. Эта тема охватывает, как и где использовать стили. Для получения информации о реализации обратитесь к [шрифту «Окружающая среда».](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)

#### <a name="bold-text"></a>Смелый текст
 Смелый текст используется экономно в Visual Studio и должен быть зарезервирован для:

- вопрос этикетки в мастеров

- назначение активного проекта в Solution Explorer

- переизугиваемые значения в окне инструмента Свойств

- некоторые события в списках редакторов Visual Basic

- содержимое, генерируемое сервером в наброске документа для веб-страниц

- заголовки разделов в сложном диалоге или дизайнерском uI

#### <a name="italics"></a>Курсив
 Visual Studio не использует ни курсив, ни смелый курсивный текст.

#### <a name="color"></a>Color

- Синий цвет зарезервирован для гиперссылок (навигация и командование) и никогда не должен использоваться для ориентации.

- Большие заголовки (экологический шрифт x 155% или больше) могут быть окрашены для этих целей:

  - Чтобы обеспечить визуальное обращение к подписи Visual Studio UI

  - Привлечь внимание к конкретной области

  - Чтобы предложить облегчение от стандартного темно-серого/черного цвета текста окружающей среды

- Цвет в заголовках должны использовать существующие цвета бренда Visual Studio, в первую очередь основной фиолетовый, #FF68217A.

- При использовании цвета в заголовках, вы должны придерживаться [принципов цвета Windows,](/windows/desktop/uxguide/vis-color)включая соотношение контрастности и другие соображения доступности.

### <a name="font-size"></a>Размер шрифта
 Дизайн визуальной студии uI имеет более легкий внешний вид с большим количеством белого пространства. Там, где это возможно, хром и титульные батончики были уменьшены или удалены. В то время как плотность информации является требованием в Visual Studio, типография по-прежнему имеет важное значение, с акцентом на более открытые интервалы между линиями и изменение размеров шрифтов и весов.

 Таблицы ниже включает в себя детали дизайна и визуальные примеры для шрифтов дисплея, используемых в Visual Studio. Некоторые вариации шрифта отображения имеют как размер, так и вес, такие как Semilight или Light, закодированные в их внешний вид.

 Фрагменты кода реализации для всех шрифтов отображения можно найти в [ссылке Formatting (масштабирование/смазывание).](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)

#### <a name="375-environment-font--light"></a>375% Окружающая среда шрифта

|||
|-|-|
|**Использование:** Редких. Уникальный фирменный только uI.<br /><br /> **Делать:**<br /><br /> - Использование приговора случае<br />- Всегда используйте легкий вес<br /><br /> **Не надо:**<br /><br /> - Использование для uI, кроме подписного uI, например Start Page<br />- Смелый, курсив, или смелый курсив<br />- Использование для текста тела<br />- Использование в окнах инструментов|**Появляется как:** 34 pt Segoe UI Light<br /><br /> **Визуальный пример:**<br /><br /> *В настоящее время не используется. Может быть использован в Visual Studio 2017 Старт Пейдж.*|

#### <a name="310-environment-font--light"></a>310% Окружающая среда шрифта

::: moniker range="vs-2017"

|||
|-|-|
|**Использования:**<br /><br /> - Большая заголовок в подписных диалогах<br />- Основной отчет заголовок<br /><br /> **Делать:**<br /><br /> - Использование приговора случае<br />- Всегда используйте легкий вес<br /><br /> **Не надо:**<br /><br /> - Использование для uI, кроме подписного uI, например Start Page<br />- Смелый, курсив, или смелый курсив<br />- Использование для текста тела<br />- Использование в окнах инструментов|**Появляется как:** 28 pt Segoe UI Light<br /><br /> **Визуальный пример:**<br /><br /> ![Пример 310% Окружающая среда шрифт &#43; Свет заголовок](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|||
|-|-|
|**Использования:**<br /><br /> - Большая заголовок в подписных диалогах<br />- Основной отчет заголовок<br /><br /> **Делать:**<br /><br /> - Использование приговора случае<br />- Всегда используйте легкий вес<br /><br /> **Не надо:**<br /><br /> - Использование для uI, кроме подписного uI<br />- Смелый, курсив, или смелый курсив<br />- Использование для текста тела<br />- Использование в окнах инструментов|**Появляется как:** 28 pt Segoe UI Light<br /><br /> **Визуальный пример:**<br /><br /> ![Пример 310% Окружающая среда шрифт &#43; Свет заголовок](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>200% Окружающая среда шрифта

|||
|-|-|
|**Использования:**<br /><br /> - Подзаголовки<br />- Названия в малых и средних диалогах<br /><br /> **Делать:**<br /><br /> - Использование приговора случае<br />- Всегда используйте полулегкий вес<br /><br /> **Не надо:**<br /><br /> - Смелый, курсив, или смелый курсив<br />- Использование для текста тела<br />- Использование в окнах инструментов|**Появляется как:** 18 pt Segoe UI Semillight<br /><br /> **Визуальный пример:**<br /><br /> ![Пример 200% шрифта окружающей среды &#43; Полулайт](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>155% Шрифт окружающей среды

|||
|-|-|
|**Использования:**<br /><br /> - Раздел заголовки в документе хорошо UI<br />- Отчеты<br /><br /> **Делать:** Использование приговора случае<br /><br /> **Не надо:**<br /><br /> - Смелый, курсив, или смелый курсив<br />- Использование для текста тела<br />- Использование в стандартных элементах управления Visual Studio<br />- Использование в окнах инструментов|**Появляется как:** 14 pt Segoe UI<br /><br /> **Визуальный пример:**<br /><br /> ![Пример шрифта заголовка 155 %, используемого в среде](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>133% Шрифт окружающей среды

|||
|-|-|
|**Использования:**<br /><br /> - Меньшие подзаголовки в подписных диалогах<br />- Меньшие подзаголовки в документе хорошо UI<br /><br /> **Делать:** Использование приговора случае<br /><br /> **Не надо:**<br /><br /> - Смелый, курсив, или смелый курсив<br />- Использование для текста тела<br />- Использование в стандартных элементах управления Visual Studio<br />- Использование в окнах инструментов|**Появляется как:** 12 pt Segoe UI<br /><br /> **Визуальный пример:**<br /><br /> ![Пример шрифта заголовка 133 %, используемого в среде](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>122% Окружающая среда шрифт

|||
|-|-|
|**Использования:**<br /><br /> - Раздел заголовки в подписи диалогов<br />- Верхние узлы в представлении дерева<br />- Вертикальная навигация вкладок<br /><br /> **Делать:** Использование приговора случае<br /><br /> **Не надо:**<br /><br /> - Смелый, курсив, или смелый курсив<br />- Использование для текста тела<br />- Использование в стандартных элементах управления Visual Studio<br />- Использование в окнах инструментов|**Появляется как:** 11 pt Segoe UI<br /><br /> **Визуальный пример:**<br /><br /> ![Пример шрифта заголовка 122 %, используемого в среде](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Шрифт окружающей среды и жирный

|||
|-|-|
|**Использования:**<br /><br /> - Этикетки и подмыки в подписных диалогах<br />- Этикетки и поднамы в отчетах<br />- Этикетки и подмыки в документе хорошо UI<br /><br /> **Делать:**<br /><br /> - Использование приговора случае<br />- Используйте смелый вес<br /><br /> **Не надо:**<br /><br /> - курсивный или смелый курсив<br />- Использование для текста тела<br />- Использование в стандартных элементах управления Visual Studio<br />- Использование в окнах инструментов|**Появляется как:** смелый 9 pt Segoe UI<br /><br /> **Визуальный пример:**<br /><br /> ![Пример шрифта окружающей среды &#43; смелейшее заголовок](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Шрифт окружающей среды

|||
|-|-|
|**Использование:** Весь другой текст<br /><br /> **Делать:** Использование приговора случае<br /><br /> **Не надо:** курсивили или смелые курсивом|**Появляется как:** 9 pt Segoe UI<br /><br /> **Визуальный пример:**<br /><br /> ![Пример шрифта среды разработки](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Обивка и интервалы
 Заголовки требуют пространства вокруг них, чтобы дать им соответствующий акцент. Это пространство варьируется в зависимости от размера точки и того, что еще находится рядом с заголовком, например горизонтального правила или строки текста в шрифте среды.

- Идеальная обивка для заголовка сама по себе должна быть 90% от пространства высоты столичного персонажа. Например, 28 pt Segoe UI Light заголовок имеет крышку высотой 26 pt, и обивка должна быть примерно 23 pt, или около 31 пикселей.

- Минимальное пространство вокруг заголовка должно сосупролеть 50% от высоты столичного символа. Меньше места может быть использовано, когда заголовок сопровождается правилом или другим плотно прилегающим элементом.

- Смелый текст шрифта среды должен следовать интервалу между высотой линии по умолчанию и обивкой.

## <a name="see-also"></a>См. также

- [MSDN: Шрифты (Windows)](/windows/desktop/uxguide/vis-fonts)
- [MSDN: Текст пользовательского интерфейса (Windows)](/windows/desktop/uxguide/text-ui)
