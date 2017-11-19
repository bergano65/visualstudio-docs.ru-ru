---
title: "Пошаговое руководство: Структурирование | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f503d9e8b0ef125fdb72ea60a9928f308b900993
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-outlining"></a>Пошаговое руководство: структурирование
Можно реализовать функции, основанный на языке, такие как структурирование, определив типы области текста, который вы хотите развернуть или свернуть. Можно определить области в контекст языковой службы, можно определить тип имени собственного файла расширения и содержимое и применить только к этому типу определение области или области определения можно применить к существующий тип содержимого (например, «текст»). В этом пошаговом руководстве показано, как для определения и отображения областей структуры.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX. Присвойте решению имя `OutlineRegionTest`.  
  
2.  Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создания расширения с помощью шаблона элемента редактор](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
## <a name="implementing-an-outlining-tagger"></a>Реализация разметчика структурирования  
 Отметить областей структуры типа тегов (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Этот тег предоставляет стандартный структурирование поведение. Указанные области можно разворачивать и сворачивать. Скрытый участок помечен знак «плюс», если он свернут, или минус, если он развернут и развернутой области, обозначенного вертикальной линии.  
  
 Ниже показано, как определить создания тегов, который создает областей структуры для всех регионов, разделенные «[» и «]».  
  
#### <a name="to-implement-an-outlining-tagger"></a>Для реализации структурирования создания тегов  
  
1.  Добавьте файл класса и назовите его `OutliningTagger`.  
  
2.  Импортируйте следующие пространства имен.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  Создайте класс с именем `OutliningTagger`, и его реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  Добавьте поля для отслеживания текстового буфера и моментальных снимков и накапливать наборы строк, которые должен быть отмечен как областей структуры. Этот код содержит список объектов области (Чтобы задать более поздней версии), которые представляют области структуры.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  Добавьте разметчика конструктор, который инициализирует поля, анализирует буфера и добавляет обработчик событий для <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> события.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> распространяется на метод, который создает тег. В этом примере предполагается, что диапазоны <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> передан методу являются смежными, несмотря на то, что это не всегда может быть так. Этот метод создает новый тег диапазон для каждой из областей структуры.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  Объявите `TagsChanged` обработчика событий.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  Добавить `BufferChanged` обработчик событий, который отвечает на <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> события путем синтаксического анализа текстового буфера.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. Добавьте метод, который выполняет синтаксический анализ буфера. В данном разделе приведен только для иллюстрации. Он синхронно выполняет синтаксический анализ буфера вложенных областей структуры.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. Следующий вспомогательный метод возвращает целое число, представляющее уровень структурирования, таким образом, 1 — пара крайней левой скобки.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. Следующий вспомогательный метод транслирует SnapshotSpan область (определяется далее в этом разделе).  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. Ниже приведен только для иллюстрации. Он определяет класс PartialRegion, который содержит номер строки и смещение начала область структуры, а также ссылку на родительский область (если таковые имеются). Это позволяет средству синтаксического анализа, настроить вложенные структурные области. Производный класс область содержит ссылку на номер строки в конец область структуры.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## <a name="implementing-a-tagger-provider"></a>Реализация поставщика разметчика  
 Для создания вашего тегов, необходимо экспортировать поставщика разметчика. Создает поставщика разметчика `OutliningTagger` для буфера, тип содержимого «text» или else возвращает `OutliningTagger` если буфер уже существует.  
  
#### <a name="to-implement-a-tagger-provider"></a>Реализация поставщика разметчика  
  
1.  Создайте класс с именем `OutliningTaggerProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>и экспортировать его с атрибутами ContentType и TagType.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> метод путем добавления `OutliningTagger` к свойствам буфера.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы проверить код, выполните сборку решения OutlineRegionTest и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Для построения и тестирования решения OutlineRegionTest  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создание текстового файла. Введите текст, который включает в себя открывающей фигурной скобки и закрывающей фигурной скобки.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Должна существовать область структуры, включающий оба фигурные скобки. Вы сможете щелкните знак «минус» слева от открывающую фигурную скобку, чтобы свернуть область структуры. Если область свернута, знак многоточия (...) должен находиться слева свернутой области, а всплывающее окно, содержащее текст **текст при наведении** должны отображаться навести указатель мыши на кнопку с многоточием.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)