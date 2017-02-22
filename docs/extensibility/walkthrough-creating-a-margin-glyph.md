---
title: "Пошаговое руководство: Создание глифа поля | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] Новинка — поля глифов"
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# Пошаговое руководство: Создание глифа поля
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно настроить внешний вид редактора полей с помощью расширения пользовательского редактора. В этом пошаговом руководстве помещает пользовательского глифа индикаторов всякий раз, когда отображается слово «todo» в комментарии к коду.  
  
## Обязательные компоненты  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Для получения дополнительной информации см. [Установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Создание проекта MEF  
  
1.  Создайте проект VSIX C\#. \(В **Новый проект** диалогового окна выберите **Visual C\# и расширяемость**, затем **проект VSIX**.\) Присвойте решению имя `TodoGlyphTest`.  
  
2.  Добавьте элемент проекта редактора классификатора. Дополнительные сведения см. в разделе [Создание расширения с помощью редактора шаблона элемента](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
## Определение глифа  
 Определите глиф, реализовав <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> интерфейса.  
  
#### Чтобы определить глифа  
  
1.  Добавьте файл класса с именем `TodoGlyphFactory`.  
  
2.  Добавьте следующий код с помощью объявлений.  
  
     [!code-cs[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  Добавьте класс с именем `TodoGlyphFactory` реализующий <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-cs[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  Добавьте закрытое поле, которое определяет измерений глифа.  
  
     [!code-cs[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  Реализуйте `GenerateGlyph` путем определения элемента глиф пользовательского интерфейса \(UI\).`TodoTag` определяется позже в этом пошаговом руководстве.  
  
     [!code-cs[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  Добавьте класс с именем `TodoGlyphFactoryProvider` реализующий <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Экспортировать класс с <xref:Microsoft.VisualStudio.Utilities.NameAttribute> из «TodoGlyph» <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> из VsTextMarker после <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «код» и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> из TodoTag.  
  
     [!code-cs[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  Реализация <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> метода путем создания экземпляра `TodoGlyphFactory`.  
  
     [!code-cs[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## Определение тега списка дел и создания тегов  
 Определите связь между элемент пользовательского интерфейса, который определен в предыдущих шагах и индикаторов, создавая тип тега и создания тегов и экспорт с помощью поставщика создания тегов.  
  
#### Для определения тега списка дел и создания тегов  
  
1.  Добавьте новый файл класса в проект и назовите его `TodoTagger`.  
  
2.  Добавьте следующие операторы imports.  
  
     [!code-cs[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  Добавьте класс с именем `TodoTag`.  
  
     [!code-cs[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  Измените класс с именем `TodoTagger` реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> типа `TodoTag`.  
  
     [!code-cs[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  Для `TodoTagger` класса, добавьте закрытые поля для <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> и текст для поиска в классификации диапазонами.  
  
     [!code-cs[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  Добавьте конструктор, который задает классификатора.  
  
     [!code-cs[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  Реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метода путем нахождения всех классификации охватывает, имена которых содержат слово «комментарий» и, текст которых содержит искомый текст. При обнаружении искомого текста обратно yield новый <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> типа `TodoTag`.  
  
     [!code-cs[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  Объявите `TagsChanged` события.  
  
     [!code-cs[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. Добавьте класс с именем `TodoTaggerProvider` реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «код» и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> из TodoTag.  
  
     [!code-cs[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. Импорт <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-cs[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. Реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> метода путем создания экземпляра `TodoTagger`.  
  
     [!code-cs[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## Сборка и тестирование кода  
 Чтобы проверить код, создания TodoGlyphTest решения и запустите его в экспериментальном экземпляре.  
  
#### Для построения и тестирования решений TodoGlyphTest  
  
1.  Постройте решение.  
  
2.  Запустите проект, нажав клавишу F5. Создается второй экземпляр Visual Studio.  
  
3.  Убедитесь, что отображается в поле индикаторов. \(На **средства** меню, щелкните **Параметры**. На **Текстовый редактор** страницы, убедитесь, что **индикаторов** выбран.\)  
  
4.  Откройте файл кода, который содержит комментарии. Добавьте слово «todo» в разделах комментарий.  
  
5.  Упрощенное синий круг с темно синий контур появятся в поле индикаторов слева от окна кода.