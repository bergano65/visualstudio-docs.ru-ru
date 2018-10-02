---
title: 'Пошаговое руководство: Структурирование | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6737d9fffa1f0f38fab57edd4031647d0cc1510e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568986"
---
# <a name="walkthrough-outlining"></a>Пошаговое руководство. Структурирование
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Пошаговое руководство: структурирование](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-outlining).  
  
Вы можете реализовать функции на основе языка, такие как структурирование, определив типы областей текста, которые вы хотите развернуть или свернуть. Можно определить регионы в контексте службы языка, можно определить тип имени собственного файла расширения и содержимого и применить определение области только этот тип или определения области можно применить в существующий тип содержимого (например, «text»). В этом пошаговом руководстве показано, как для определения и отображения областей структуры.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX. Назовите решение `OutlineRegionTest`.  
  
2.  Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
## <a name="implementing-an-outlining-tagger"></a>Реализация структуры средство создания тегов  
 Отметить областей структуры типа тегов (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Этот тег содержит стандартный структурирование поведение. Области можно разворачивать и сворачивать. Области помечается знак "плюс", если он свернут, или минус, если он развернут и развернутой области, обозначенного вертикальной линией.  
  
 Ниже показано, как определить средство создания тегов, который создает областей структуры для всех регионов, разделенные «[» и «]».  
  
#### <a name="to-implement-an-outlining-tagger"></a>Для реализации структуры средство создания тегов  
  
1.  Добавьте файл класса и назовите его `OutliningTagger`.  
  
2.  Импортируйте следующие пространства имен.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3.  Создайте класс с именем `OutliningTagger`, и его реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4.  Добавьте поля для отслеживания текстового буфера и моментальных снимков и накапливать наборы строк, которые должны использоваться как области структуры. Этот код включает список объектов области (должна определяться более поздней версии), представляющие области структуры.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5.  Добавьте конструктор средство создания тегов, который инициализирует поля, анализирует буфера, и добавляет обработчик событий для <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> событий.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6.  Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> распространяется на метод, который создает экземпляр тега. В этом примере предполагается, что диапазоны <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> переданный в метод являются смежными, несмотря на то, что это не всегда может быть так. Этот метод создает новый диапазон с тегом для каждой из областей структуры.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7.  Объявите `TagsChanged` обработчик событий.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8.  Добавить `BufferChanged` обработчик событий, который отвечает на <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> события путем синтаксического анализа текстового буфера.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. Добавьте метод, который выполняет синтаксический анализ буфера. В приведенном ниже примере приведен исключительно для иллюстрации. Он синхронно выполняет синтаксический анализ буфера в вложенных областей структуры.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. Следующий вспомогательный метод возвращает целое число, представляющее уровень структурирования, таким образом, 1 — это пара скобок, крайнего левого.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. Следующий вспомогательный метод преобразует область (определяется далее в этом разделе) в диапазон SnapshotSpan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. Следующий код приведен исключительно для иллюстрации. Он определяет класс PartialRegion, который содержит номер строки и смещение начала область структуры, а также ссылку на родительский область (если таковые имеются). Это позволяет средству синтаксического анализа, настроить вложенных областей структуры. Производный класс областей содержит ссылку на номер строки в конце область структуры.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>Реализация поставщика разметчика  
 Его необходимо экспортировать поставщика разметчика для вашей средство создания тегов. Создает поставщика разметчика `OutliningTagger` для буфера, тип содержимого «text» или else возвращает `OutliningTagger` если буфер уже существует.  
  
#### <a name="to-implement-a-tagger-provider"></a>Реализация поставщика разметчика  
  
1.  Создайте класс с именем `OutliningTaggerProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>и экспортировать его с ContentType и TagType атрибутами.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2.  Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> метод путем добавления `OutliningTagger` к свойствам буфера.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы протестировать этот код, выполните сборку решения OutlineRegionTest и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Построение и тестирование решения OutlineRegionTest  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создание текстового файла. Введите текст, который включает в себя открывающей фигурной скобки и закрывающей фигурной скобки.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Должна существовать область структуры, включающий как фигурные скобки. Можно щелкнуть знак «минус» слева от открывающую фигурную скобку, чтобы свернуть область структуры. Если область свернута, символ многоточия (...) должен находиться слева от свернутой области, а всплывающее окно, содержащее текст **текст при наведении** должно появляться при перемещении указателя мыши на многоточие.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

