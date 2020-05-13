---
title: 'Пошаговая прогулка: Отображение подходящих скобки (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 107610733ab9b5c8085b3f987fa999250b453d63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697453"
---
# <a name="walkthrough-display-matching-braces"></a>Прохождение: Отображение соответствующих скобки
Реализация функций, основанных на языке, таких как соответствие скобки путем определения скобки вы хотите соответствовать, и добавить тег маркера текста в соответствие скобки, когда caret находится на одном из скобки. Вы можете определить скобки в контексте языка, определить свое расширение и тип содержимого имени файла, а также применить теги только к этому типу или применить теги к существующему типу содержимого (например, "текст"). Следующее пошаговое решение показывает, как применять теги соответствия скобки к типу содержимого "текст".

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Создание проекта управляемой расширительности (MEF)

#### <a name="to-create-a-mef-project"></a>Создание проекта MEF

1. Создайте проект классификатора редактора. Назовите решение `BraceMatchingTest`.

2. Добавьте шаблон элемента классификатора редактора в проект. Для получения дополнительной информации [см. Создать расширение с шаблоном элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

## <a name="implement-a-brace-matching-tagger"></a>Реализация скобки соответствия tagger
 Чтобы получить эффект выделения скобки, который напоминает тот, который используется в Visual <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>Studio, можно реализовать теггер типа. Следующий код показывает, как определить теггер для пар скобки на любом уровне вложенности. В этом примере пары скобки {} и определяются в конструкторе тегера, но в полной реализации языка соответствующие пары скобки будут определены в спецификации языка.

### <a name="to-implement-a-brace-matching-tagger"></a>Для реализации скобки соответствия tagger

1. Добавьте файл класса и назовите его BraceMatching.

2. Импортируйте следующие пространства имен.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. Определите `BraceMatchingTagger` класс, который <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> наследует от типа. <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. Добавьте свойства для представления текста, исходного буфера, текущей точки снимка, а также набора пар скобки.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. В конструкторе tagger установите свойства и подпишитесь на события <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> изменения представления и <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>: В этом примере для иллюстративных целей соответствующие пары также определяются в конструкторе.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. В рамках <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> реализации объявить событие TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. Обработчики событий обновляют текущее `CurrentChar` положение объекта и повышают событие TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. Реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метода, сочетающегося с фигурами либо при виде открытого символа, либо при близком характере, как в Visual Studio. Когда матч найден, этот метод мгновенно встречает два тега, один для открытой скобки и один для близкой скобки.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. Следующие частные методы найти соответствующие скобки на любом уровне гнездования. Первый метод находит близкий символ, который соответствует открытому символу:

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. Следующий метод помощника находит открытый символ, который соответствует близкому персонажу:

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Реализация поставщика совмещений с теггером скобки
 В дополнение к реализации tagger, вы также должны реализовать и экспортировать поставщика tagger. В этом случае тип содержимого поставщика является "текстом". Таким образом, соответствие скобки будет отображаться во всех типах текстовых файлов, но более полная реализация применяется скобки, соответствующие только определенному типу содержимого.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Для реализации поставщика совмещений с теггером скобки

1. Объявить поставщика tagger, <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>который наследует от , назовите <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> его BraceMatchingTaggerProvider, и экспортировать его с "текст" и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> . <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. Реализация <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> метода мгновенного приготовления BraceMatchingTagger.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Создание и тестирование кода
 Чтобы протестировать этот код, создайте решение BraceMatchingTest и запустите его в экспериментальном экземпляре.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Создание и тестирование решения BraceMatchingTest

1. Создайте решение.

2. При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

3. Создайте текстовый файл и введите текст, который включает в себя соответствующие скобки.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. При располагаться карета перед открытой скобкой, следует выделить как скобки, так и соответствующие близкие скобки. При расположении курсора сразу после закрытия скобки, как скобки и соответствующие открытые скобки должны быть выделены.

## <a name="see-also"></a>См. также
- [Прохождение: Свяжите тип содержимого с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
