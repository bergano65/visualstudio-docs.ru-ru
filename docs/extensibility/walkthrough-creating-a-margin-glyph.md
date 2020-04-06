---
title: 'Пошаговая прогулка: Создание маржинальный глиф Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9588b150dd795fc2bc5e6c55d8f6e2359f609939
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697702"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Прохождение: Создать маржиглиф
Вы можете настроить внешний вид поля редактора с помощью пользовательских расширений редактора. Это пошаговое решение помещает пользовательский глиф на маржу индикатора всякий раз, когда слово "todo" появляется в комментарии к коду.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Создание проекта MEF

1. Создайте проект СЗ VSIX. (В **диалоге нового проекта** выберите **Visual C / Расширяемость,** затем **VSIX Project**.) Назовите решение. `TodoGlyphTest`

2. Добавьте элемент проекта классификатора редактора. Для получения дополнительной информации [см. Создать расширение с шаблоном элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

## <a name="define-the-glyph"></a>Определите глиф
 Определите глиф, запустив <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> интерфейс.

### <a name="to-define-the-glyph"></a>Определить глиф

1. Добавьте файл класса с именем `TodoGlyphFactory`.

2. Добавьте следующий код, используя декларации.

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. Добавьте класс, названный, `TodoGlyphFactory` который <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>реализуется.

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. Добавьте частное поле, определяющее размеры глифа.

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. Реализация `GenerateGlyph` путем определения элемента пользовательского интерфейса glyph (UI). `TodoTag`определяется позже в этом пошаговом пошаговом пошаге.

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. Добавьте класс, названный, `TodoGlyphFactoryProvider` который <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>реализуется. Экспортировать этот <xref:Microsoft.VisualStudio.Utilities.NameAttribute> класс с "TodoGlyph", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> после VsTextMarker, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "код", <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> и TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. Реализация <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> метода путем мгновенного `TodoGlyphFactory`.

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>Определение тега Todo и тегетера
 Определите взаимосвязь между элементом uI, определяемым на предыдущих этапах, и маржой индикатора. Создайте тип тега и теггер и экспортите его с помощью поставщика tagger.

### <a name="to-define-a-todo-tag-and-tagger"></a>Определить тег и теги todo

1. Добавьте новый файл класса в `TodoTagger`проект и назовите его.

2. Добавьте приведенные ниже импортированные данные.

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. Добавьте класс с именем `TodoTag`.

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. Измените класс, `TodoTagger` <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> названный, `TodoTag`который реализует тип.

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. В `TodoTagger` класс добавьте частные <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> поля для и для текста, чтобы найти в диапазоне классификации.

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. Добавьте конструктор, который устанавливает классификатор.

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метод, найдя все диапазоны классификаций, имена которых включают слово "комментарий" и текст которого включает текст поиска. Всякий раз, когда поиск текст <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> найден, `TodoTag`уступить новый тип .

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. Объявить `TagsChanged` событие.

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. Добавьте класс `TodoTaggerProvider` с <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>именем, который <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> реализует, и экспортировать его с "кодом" и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. Импорт <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. Реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> метода путем мгновенного `TodoTagger`.

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>Создание и тестирование кода
 Чтобы протестировать этот код, создайте решение TodoGlyphTest и запустите его в экспериментальном экземпляре.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Создание и тестирование решения TodoGlyphTest

1. Создайте решение.

2. Выполнить проект, нажав **F5**. Начинается второй экземпляр Visual Studio.

3. Убедитесь, что маржа индикатора отображается. (В меню **«Инструменты»** щелкните **Параметры**. На странице **редактора текста** убедитесь, что **маржа индикатора** выбрана.)

4. Откройте файл кода с комментариями. Добавьте слово "тодо" в один из разделов комментариев.

5. Светло-голубой круг с темно-синим контуром появляется в поле индикатора слева от окна кода.
