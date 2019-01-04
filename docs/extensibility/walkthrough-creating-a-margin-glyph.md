---
title: Пошаговое руководство. Создание глифа поля | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce1d3449c786211c90df52b0633c84cf2a491769
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851356"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Пошаговое руководство. Создание глифа поля
Можно настроить внешний вид поля редактора с помощью расширения пользовательского редактора. В этом пошаговом руководстве помещает пользовательского глифа в поле индикаторов, каждый раз, когда отображается слово «todo» в комментарии к коду.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не устанавливайте Visual Studio SDK в центре загрузки. Этот пакет включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалоговом окне выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Назовите решение `TodoGlyphTest`.  
  
2.  Добавьте элемент проект классификатора редактора. Дополнительные сведения см. в разделе [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
## <a name="define-the-glyph"></a>Определите глифа  
 Определите глиф, выполнив <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> интерфейс.  
  
### <a name="to-define-the-glyph"></a>Для определения глифа  
  
1.  Добавьте файл класса с именем `TodoGlyphFactory`.  
  
2.  Добавьте следующий код с помощью объявлений.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  Добавьте класс с именем `TodoGlyphFactory` , реализующий <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  Добавьте закрытое поле, которое определяет размеры глифа.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  Реализуйте `GenerateGlyph` , определяя элемент пользовательского интерфейса (UI) глифа. `TodoTag` будет рассматриваться далее в этом пошаговом руководстве.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  Добавьте класс с именем `TodoGlyphFactoryProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Экспорт этого класса с <xref:Microsoft.VisualStudio.Utilities.NameAttribute> из «TodoGlyph», <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> из после VsTextMarker <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «код» и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> из TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  Реализуйте <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> метод путем создания экземпляра `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## <a name="define-a-todo-tag-and-tagger"></a>Определение тега Todo и средство создания тегов  
 Определите связь между элементом пользовательского интерфейса, определенные на предыдущих шагах и поле индикаторов. Создание типа тега и средство создания тегов и экспортируйте его с помощью поставщика разметчика.  
  
### <a name="to-define-a-todo-tag-and-tagger"></a>Для определения тега todo и средство создания тегов  
  
1.  Добавьте новый файл класса в проект и назовите его `TodoTagger`.  
  
2.  Добавьте следующие импорты.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  Добавьте класс с именем `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  Измените класс с именем `TodoTagger` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> типа `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  Для `TodoTagger` класса, добавьте закрытые поля для <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> и текст для поиска в данной классификации диапазонами.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  Добавьте конструктор, который задает классификатора.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метод путем нахождения всех классификации охватывает, имена которых содержат слово «comment» и текст которого включает в себя текст для поиска. Каждый раз, когда найден искомый текст обратно yield новый <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> типа `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  Объявите `TagsChanged` событий.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. Добавьте класс с именем `TodoTaggerProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> из «код» и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> из TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. Импорт <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> метод путем создания экземпляра `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## <a name="build-and-test-the-code"></a>Построение и тестирование кода  
 Чтобы протестировать этот код, выполните сборку решения TodoGlyphTest и запустите его в экспериментальном экземпляре.  
  
### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Построение и тестирование решения TodoGlyphTest  
  
1.  Постройте решение.  
  
2.  Запустите проект, нажав клавишу **F5**. Запускается второй экземпляр Visual Studio.  
  
3.  Убедитесь, что отображается поле индикаторов. (На **средства** меню, щелкните **параметры**. На **текстовый редактор** странице, убедитесь, что **индикаторов** выбран.)  
  
4.  Откройте файл кода, который содержит комментариев. Добавление слова «todo» в разделах комментарий.  
  
5.  Синий круг светлой темно-синим контуром отображается в поле индикаторов слева от окна кода.