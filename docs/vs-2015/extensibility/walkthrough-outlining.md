---
title: Пошаговое руководство. структурирование | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c1dd3d28b9978b52c95b5ff905d57720ed10f5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201957"
---
# <a name="walkthrough-outlining"></a>Пошаговое руководство. Структурирование
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно реализовать языковые функции, такие как структурирование, путем определения типов текстовых областей, которые необходимо развернуть или свернуть. Можно определить регионы в контексте языковой службы или определить собственное расширение имени файла и тип содержимого, а также применить определение региона только к этому типу или применить определения областей к существующему типу содержимого (например, "Text"). В этом пошаговом руководстве показано, как определить и отобразить области структуры.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Создание проекта MEF  
  
1. Создайте проект VSIX. Назовите решение `OutlineRegionTest`.  
  
2. Добавьте шаблон элемента классификатора редактора в проект. Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Удалите файлы существующих классов.  
  
## <a name="implementing-an-outlining-tagger"></a>Реализация тегов для структурирования  
 Регионы структурирования помечены видом тега ( <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ). Этот тег обеспечивает стандартное поведение структурирования. Контурный регион можно развернуть или свернуть. Контурный регион помечается знаком «плюс», если он свернут, или знак «минус», если он развернут, а развернутая область — демаркатед вертикальной линией.  
  
 В следующих шагах показано, как определить средство создания тегов, которое создает области структуры для всех регионов, разделенных символами "[" и "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>Реализация средства создания тегов структуры  
  
1. Добавьте файл класса с именем `OutliningTagger`.  
  
2. Импортируйте следующие пространства имен.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3. Создайте класс с именем `OutliningTagger` и реализуйте его <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4. Добавьте некоторые поля для трассировки текстового буфера и моментального снимка, а также для накопления наборов строк, которые должны быть помечены как регионы структурирования. Этот код включает список объектов Region (которые будут определены позже), представляющих регионы структуры.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5. Добавьте конструктор средства создания тегов, который инициализирует поля, анализирует буфер и добавляет обработчик событий в <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> событие.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метод, который создает экземпляры диапазона тегов. В этом примере предполагается, что диапазоны, <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> переданные в метод, являются непрерывными, хотя это может быть не всегда так. Этот метод создает новый диапазон тегов для каждой из областей структуры.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7. Объявите `TagsChanged` обработчик событий.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8. Добавьте `BufferChanged` обработчик событий, реагирующий на <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> события путем синтаксического анализа текстового буфера.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. Добавьте метод, который анализирует буфер. Пример, приведенный здесь, предназначен только для иллюстрации. Он синхронно анализирует буфер во вложенные области структуры.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. Следующий вспомогательный метод получает целое число, представляющее уровень структуры, таким, что 1 — это левая пара фигурных скобок.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. Следующий вспомогательный метод преобразует область (определенную далее в этом разделе) в диапазон SnapshotSpan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. Следующий код предназначен только для иллюстрации. Он определяет класс Партиалрегион, который содержит номер строки и смещение начала области структуры, а также ссылку на родительскую область (если она есть). Это позволяет средству синтаксического анализа настраивать вложенные области структуры. Производный класс Region содержит ссылку на номер строки конца области структуры.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>Реализация поставщика тегов  
 Необходимо экспортировать поставщик тегов для создания тегов. Поставщик тегов создает `OutliningTagger` для буфера типа содержимого text, или Else возвращает, `OutliningTagger` если буфер уже имеет такой тип.  
  
#### <a name="to-implement-a-tagger-provider"></a>Реализация поставщика тегов  
  
1. Создайте класс с именем `OutliningTaggerProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , и экспортируйте его с атрибутами ContentType и тагтипе.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> метод, добавив `OutliningTagger` в свойства буфера.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы протестировать этот код, создайте решение Аутлинерегионтест и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Создание и тестирование решения Аутлинерегионтест  
  
1. Создайте решение.  
  
2. При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3. Создание текстового файла. Введите текст, включающий открывающую фигурную скобку и закрывающую фигурную скобку.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4. Должна существовать область структуры, включающая обе фигурные скобки. Чтобы свернуть область структуры, щелкните знак "минус" слева от открывающей скобки. Если область свернута, то символ многоточия (...) должен отображаться слева от свернутой области, а всплывающее окно, содержащее текст, нарисованный при **наведении** указателя на многоточие, должно отобразиться.  
  
## <a name="see-also"></a>См. также:  
 [Пошаговое руководство. Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
