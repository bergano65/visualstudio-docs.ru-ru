---
title: "Пошаговое руководство: структурирование | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] новый - структура"
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 30
---
# Пошаговое руководство: структурирование
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно реализовать функции, основанный на языке, такие как структурирование, определив типы областей текста, которые требуется развернуть или свернуть. Можно определить области в контекст языковой службы, можно определить собственный файл имя расширения или типу содержимого и определение области применить только к этому типу или определения области можно применить существующий тип содержимого \(например, «текст»\). В этом пошаговом руководстве показано, как определить и отображения областей структуры.  
  
## Обязательные компоненты  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Для получения дополнительной информации см. [Установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Создание проекта Managed Extensibility Framework \(MEF\)  
  
#### Создание проекта MEF  
  
1.  Создайте проект VSIX. Присвойте решению имя `OutlineRegionTest`.  
  
2.  Добавьте в проект шаблон элемента редактор классификатора. Для получения дополнительной информации см. [Создание расширения с помощью редактора шаблона элемента](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
## Реализация структуры создания тегов  
 Отметить областей структуры типа тегов \(<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>\). Этот тег предоставляет стандартный структурирование поведение. Указанные области можно разворачивать и сворачивать. Скрытый участок помечен знак "плюс", если он свернут или знак минус, если он развернут и развернутой области, обозначенного вертикальной линии.  
  
 Ниже показано, как определить создания тегов, который создает областей структуры для всех регионов, разделенные» \[» и «\]».  
  
#### Для реализации структурирования создания тегов  
  
1.  Добавьте файл класса с именем `OutliningTagger`.  
  
2.  Импортируйте следующие пространства имен.  
  
     [!code-cs[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  Создайте класс с именем `OutliningTagger`, и его реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-cs[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  Добавьте поля для отслеживания текстового буфера и моментальных снимков и накапливать наборы строк, которые должен быть отмечен как областей структуры. Этот код включает список объектов области \(определены в дальнейшем\), представляющие области структуры.  
  
     [!code-cs[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  Добавьте создания тегов конструктор, который инициализирует поля, анализирует буфера и добавляет обработчик событий для <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> события.  
  
     [!code-cs[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> распространяется на метод, который создает тег. В этом примере предполагается, что диапазоны <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> передан методу являются смежными, хотя это не всегда может быть так. Этот метод создает новый диапазон с тегом для всех областей структуры.  
  
     [!code-cs[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  Объявите `TagsChanged` обработчика событий.  
  
     [!code-cs[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  Добавление `BufferChanged` обработчик события, реагирующий на <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> события путем синтаксического анализа текстового буфера.  
  
     [!code-cs[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. Добавьте метод, который выполняет синтаксический анализ буфера. В приведенном ниже примере — только для иллюстрации. Синхронно, он анализирует буфера в вложенных областей структуры.  
  
     [!code-cs[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. Следующий вспомогательный метод возвращает целое число, представляющее уровень структурирования, таким образом, 1 — пара крайней левой фигурной скобки.  
  
     [!code-cs[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. Следующий вспомогательный метод означает SnapshotSpan регион \(определено далее в этом разделе\).  
  
     [!code-cs[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. Ниже приведен только для иллюстрации. Он определяет класс PartialRegion, который содержит номер строки и смещение начала область структуры, а также ссылку на родительской области \(если таковые имеются\). Это позволяет средству синтаксического анализа, настроить вложенных областей структуры. Производный класс Region содержит ссылку на номер строки в конце область структуры.  
  
     [!code-cs[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## Реализация поставщика создания тегов  
 Для создания вашего тегов необходимо экспортировать поставщика создания тегов. Создает поставщик создания тегов `OutliningTagger` для буфера, тип содержимого «text» или else возвращает `OutliningTagger` Если буфер уже существует.  
  
#### Для реализации поставщика создания тегов  
  
1.  Создайте класс с именем `OutliningTaggerProvider` реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, и экспортировать его атрибутами ContentType и TagType.  
  
     [!code-cs[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  Реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> метода, добавив `OutliningTagger` к свойствам буфера.  
  
     [!code-cs[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## Сборка и тестирование кода  
 Чтобы проверить код, создания OutlineRegionTest решения и запустите его в экспериментальном экземпляре.  
  
#### Для построения и тестирования решений OutlineRegionTest  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создание текстового файла. Введите текст, который включает в себя открывающей фигурной скобки и закрывающую фигурную скобку.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Должна существовать область структуры, включающий оба фигурные скобки. Вы сможете щелкните знак «минус» слева от открывающую фигурную скобку, чтобы свернуть область структуры. Если область свернута, знак многоточия \(...\) должен находиться слева свернутой области и всплывающее окно, содержащее текст **текст при наведении** должен отображаться при наведении указателя мыши на кнопку с многоточием.  
  
## См. также  
 [Пошаговое руководство: Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)