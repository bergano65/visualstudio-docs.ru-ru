---
title: "Пошаговое руководство: Создание глиф поле | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fc813ed3c29c2fe0a4cac1c348ffed18ae8fd2d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-margin-glyph"></a>Пошаговое руководство: Создание глиф поля
Можно настроить внешний вид редактора полей с помощью расширений специализированный редактор. В этом пошаговом руководстве помещает пользовательских глифов на поле индикатора всякий раз, когда отображается слово «todo» в комментарии к коду.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалогового окна выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Присвойте решению имя `TodoGlyphTest`.  
  
2.  Добавьте элемент проект классификатора редактора. Дополнительные сведения см. в разделе [создания расширения с помощью шаблона элемента редактор](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
## <a name="defining-the-glyph"></a>Определение глифа  
 Определите глиф, реализовав <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> интерфейса.  
  
#### <a name="to-define-the-glyph"></a>Для определения глифа  
  
1.  Добавьте файл класса и назовите его `TodoGlyphFactory`.  
  
2.  Добавьте следующий код с помощью объявлений.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  Добавьте класс с именем `TodoGlyphFactory` , реализующий <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  Добавьте закрытое поле, которое определяет измерений глифа.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  Реализуйте `GenerateGlyph` путем определения элемента пользовательского интерфейса (UI) глифа. `TodoTag`определяется позже в этом пошаговом руководстве.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  Добавьте класс с именем `TodoGlyphFactoryProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Экспортировать класс с <xref:Microsoft.VisualStudio.Utilities.NameAttribute> из «TodoGlyph» <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> из после VsTextMarker <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «код» и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> из TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  Реализуйте <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> метод путем создания экземпляра `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Определение тег Todo и создания тегов  
 Определите связь между элемент пользовательского интерфейса, который определен в предыдущих шагах, а поле индикаторов, создавая тип тега и создания тегов и их экспорта с помощью поставщика разметчика.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Для определения тег todo и создания тегов  
  
1.  Добавьте новый файл класса в проект и назовите его `TodoTagger`.  
  
2.  Добавьте следующие операторы imports.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  Добавьте класс с именем `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  Измените класс с именем `TodoTagger` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> типа `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  Чтобы `TodoTagger` класса, добавьте закрытые поля для <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> и текст для поиска в данной классификации диапазонами.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  Добавьте конструктор, который задает классификатора.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метод, который можно найти все классификации охватывает, имена которых содержат слово «комментарий» и, текст которых содержит искомый текст. Каждый раз, когда найден искомый текст обратно yield новый <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> типа `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  Объявите `TagsChanged` событий.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. Добавьте класс с именем `TodoTaggerProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «код» и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> из TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. Импорт <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> метод путем создания экземпляра `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы проверить код, выполните сборку решения TodoGlyphTest и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Для построения и тестирования решения TodoGlyphTest  
  
1.  Постройте решение.  
  
2.  Запустите проект, нажав клавишу F5. Создается второй экземпляр Visual Studio.  
  
3.  Убедитесь, что отображается поле индикаторов. (На **средства** меню, нажмите кнопку **параметры**. На **текстовый редактор** убедитесь, что **индикаторов** выбран.)  
  
4.  Откройте файл кода, содержащий комментарии. Добавление слова «todo» в разделах Примечание.  
  
5.  Светлая синий круг с темной синий контур должны появиться в поле индикаторов слева от окна кода.