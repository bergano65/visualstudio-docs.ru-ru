---
title: Пошаговое руководство. Структурирование | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 908b2f2b7a0dc055065abd96df3eb4495ad30ce8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965058"
---
# <a name="walkthrough-outlining"></a>Пошаговое руководство. Структуризация
Настройка компонентов на основе языка, такие как структурирование, определив типы областей текста, которые вы хотите развернуть или свернуть. Можно определения областей в контексте языковую службу, или определить тип имени собственного файла расширения и содержимого и применяются только к этому типу определение области или применить область определения в существующий тип содержимого (например, «text»). В этом пошаговом руководстве показано, как для определения и отображения областей структуры.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, не устанавливайте Visual Studio SDK в центре загрузки. Этот пакет включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)

### <a name="to-create-a-mef-project"></a>Создание проекта MEF

1. Создайте проект VSIX. Назовите решение `OutlineRegionTest`.

2. Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

## <a name="implement-an-outlining-tagger"></a>Реализация структуры средство создания тегов
 Отметить областей структуры типа тегов (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Этот тег содержит стандартный структурирование поведение. Области можно разворачивать и сворачивать. Области помечен знак плюса (**+**), если он свернут или "минус" (**-**) если он развернут и развернутой области, обозначенного вертикальной линией.

 Ниже показано, как определить средство создания тегов, который создает областей структуры для всех регионов, заключены в квадратные скобки (**[**,**]**).

### <a name="to-implement-an-outlining-tagger"></a>Для реализации структуры средство создания тегов

1. Добавьте файл класса с именем `OutliningTagger`.

2. Импортируйте следующие пространства имен.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. Создайте класс с именем `OutliningTagger`, и его реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. Добавьте поля для отслеживания текстового буфера и моментальных снимков и накапливать наборы строк, которые должны использоваться как области структуры. Этот код включает список объектов области (должна определяться более поздней версии), представляющие области структуры.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. Добавьте конструктор средство создания тегов, который инициализирует поля, анализирует буфера, и добавляет обработчик событий для <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> событий.

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> распространяется на метод, который создает экземпляр тега. В этом примере предполагается, что диапазоны <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> переданный в метод являются смежными, несмотря на то, что он не всегда может быть так. Этот метод создает новый диапазон с тегом для каждой из областей структуры.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. Объявите `TagsChanged` обработчик событий.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. Добавить `BufferChanged` обработчик событий, который отвечает на <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> события путем синтаксического анализа текстового буфера.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. Добавьте метод, который выполняет синтаксический анализ буфера. В приведенном ниже примере приведен исключительно для иллюстрации. Он синхронно выполняет синтаксический анализ буфера в вложенных областей структуры.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. Следующий вспомогательный метод возвращает целое число, представляющее уровень структурирования, таким образом, 1 — это пара скобок, крайнего левого.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. Следующий вспомогательный метод преобразует область (определяется далее в этой статье) в диапазон SnapshotSpan.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. Следующий код приведен исключительно для иллюстрации. Он определяет класс PartialRegion, который содержит номер строки и смещение начала область структуры, а также ссылку на родительский область (если таковые имеются). Этот код позволяет средству синтаксического анализа, настроить вложенных областей структуры. Производный класс областей содержит ссылку на номер строки в конце область структуры.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>Реализация поставщика разметчика
 Экспортируйте поставщик средство создания тегов для вашей средство создания тегов. Создает поставщика разметчика `OutliningTagger` для буфера, тип содержимого «text» или else возвращает `OutliningTagger` если буфер уже существует.

### <a name="to-implement-a-tagger-provider"></a>Реализация поставщика разметчика

1. Создайте класс с именем `OutliningTaggerProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>и экспортировать его с ContentType и TagType атрибутами.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> метод путем добавления `OutliningTagger` к свойствам буфера.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>Построение и тестирование кода
 Чтобы протестировать этот код, выполните сборку решения OutlineRegionTest и запустите его в экспериментальном экземпляре.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Построение и тестирование решения OutlineRegionTest

1. Постройте решение.

2. При запуске этого проекта в отладчике, запускается второй экземпляр Visual Studio.

3. Создание текстового файла. Введите текст, который включает в себя как открывающие скобки, так и закрывающие скобки.

    ```
    [
       Hello
    ]
    ```

4. Должна существовать область структуры, включает в себя оба квадратные скобки. Можно щелкнуть знак «минус» слева от открывающей скобки, чтобы свернуть область структуры. Если область свернута, символ многоточия (*...* ) должен находиться слева от свернутой области, а всплывающее окно, содержащее текст **текст при наведении** должно появляться при перемещении указателя мыши на многоточие.

## <a name="see-also"></a>См. также
- [Пошаговое руководство: Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)