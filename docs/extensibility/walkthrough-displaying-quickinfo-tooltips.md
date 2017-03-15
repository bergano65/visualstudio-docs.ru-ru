---
title: "Пошаговое руководство: Отображение кратких сведений подсказки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b533e77a2310194b2bccc225f9902e5a8d502da5
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Пошаговое руководство: Отображение кратких сведений подсказки
Краткие сведения о является функцией IntelliSense, отображающий сигнатуры метода и описания, когда пользователь перемещает указатель на имя метода. Язык на основе функции, такие как кратких сведений можно реализовать путем определения идентификаторов, для которых требуется предоставить описания кратких сведений, а затем создать подсказку для отображения содержимого. Кратких сведений можно определить в контекст языковой службы, можно определить собственный файл имя расширения или типу содержимого и отображение кратких сведений для только этот тип или можно отобразить кратких сведений для существующего типа контента (например, «текст»). В этом пошаговом руководстве демонстрируется отображение кратких сведений для типа содержимого «text».  
  
 В примере кратких сведений в этом пошаговом руководстве отображает подсказки при наведении указателя мыши на имени метода. Такой подход требует реализации этих четырех интерфейсов:  
  
-   исходный интерфейс  
  
-   интерфейс поставщика источника  
  
-   интерфейс контроллера  
  
-   контроллер интерфейса поставщика  
  
 Поставщики источника и контроллера являются компоненты Managed Extensibility Framework (MEF) и отвечают за экспортирование классов источника и контроллера и импорт служб является посредником при таких как <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, и создается текстовый буфер подсказки и <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, который запускает сеанс кратких сведений.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> </xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>  
  
 В этом примере источник кратких сведений использует жестко закодированный список имен методов и описания, но в полной реализации службы языка и документации по языку несут ответственность за предоставление этого содержимого.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
#### <a name="to-create-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалогового окна выберите **Visual C# и расширяемость**, затем **проект VSIX**.) Присвойте решению имя `QuickInfoTest`.  
  
2.  Добавьте в проект шаблон элемента редактор классификатора. Дополнительные сведения см. в разделе [создания расширения с помощью редактора шаблона элемента](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
## <a name="implementing-the-quickinfo-source"></a>Реализация источника кратких сведений  
 Источник кратких сведений отвечает за сбор набор идентификаторов и их описания и добавление содержимого буфера текст всплывающей подсказки при появлении один из идентификаторов. В этом примере идентификаторы и их описание только что добавили в конструкторе источника.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Для реализации источника кратких сведений  
  
1.  Добавьте файл класса с именем `TestQuickInfoSource`.  
  
2.  Добавьте ссылку на Microsoft.VisualStudio.Language.IntelliSense.  
  
3.  Добавьте следующие операторы imports.  
  
     [!code-vb[#1 VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#1;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  Объявите класс, который реализует <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>и назовите его `TestQuickInfoSource`.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
     [!code-vb[VSSDKQuickInfoTest&2;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#2;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  Добавление полей для кратких сведений поставщика источника, текстовом буфере и набор метод имена и подписи методов. В этом примере имена и подписи методов инициализируются в `TestQuickInfoSource` конструктора.  
  
     [!code-vb[VSSDKQuickInfoTest&3;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#3;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  Добавьте конструктор, который задает поставщик источника кратких сведений и текстовый буфер и заполняет набор имен методов и подписи методов и описания.  
  
     [!code-vb[#4 VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#4;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>метода.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> В этом примере метод находит слово текущего или предыдущего слова, если курсор находится в конце строки или текстового буфера. Если слово является одним из имен методов, описание для этого имени метода добавляется содержимое кратких сведений.  
  
     [!code-vb[#5 VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#5;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  Также необходимо реализовать метод Dispose(), поскольку <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>реализует <xref:System.IDisposable>:</xref:System.IDisposable> </xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
     [!code-vb[VSSDKQuickInfoTest&6;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&6;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Реализация поставщика источника кратких сведений  
 Поставщик источника кратких сведений служит главным образом для экспортировать сама себя в качестве компонента MEF и создать источник кратких сведений. Так как он является частью компонента MEF, он может импортировать других частей компонента MEF.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Для реализации поставщика источника кратких сведений  
  
1.  Объявите поставщик источника кратких сведений, с именем `TestQuickInfoSourceProvider` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.NameAttribute>«Подсказка кратких сведений источника» <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>из ранее = «по умолчанию» и <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>«текст».</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.OrderAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
     [!code-vb[#7 VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#7;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  Импорт две службы редактора <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>и <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, как свойства `TestQuickInfoSourceProvider`.</xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>  
  
     [!code-vb[№&8; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb) ] 
     [!code-cs [VSSDKQuickInfoTest №&8;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>возвращается новый `TestQuickInfoSource`.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>  
  
     [!code-vb[№&9; VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb) ] 
     [!code-cs [VSSDKQuickInfoTest №&9;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Реализация контроллера кратких сведений  
 Краткие сведения о контроллеры определяют, когда должны отображаться кратких сведений. В этом примере кратких сведений отображается, когда указатель находится над слово, которое соответствует имени метода. Краткие сведения о контроллере реализует обработчик событий мыши при наведении указателя мыши, которое запускает сеанс кратких сведений.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Для реализации контроллера кратких сведений  
  
1.  Объявите класс, который реализует <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>и назовите его `TestQuickInfoController`.</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>  
  
     [!code-vb[#10 VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#10;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  Добавьте закрытые поля для представления текста текстовых буферах, представлены в текстовое представление, сеанс кратких сведений и поставщиком контроллера кратких сведений.  
  
     [!code-vb[#11 VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#11;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  Добавьте конструктор, который устанавливает полей и добавляет обработчик события наведения мыши.  
  
     [!code-vb[#12 VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#12;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  Добавьте обработчик событий мыши при наведении указателя мыши, которое запускает сеанс кратких сведений.  
  
     [!code-vb[#13 VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#13;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>метода, так что он удаляет обработчик события наведения мыши при отсоединении контроллер из текстового представления.</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>  
  
     [!code-vb[#14 VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#14;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>метода и <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A>метод как пустые методы для этого примера.</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> </xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>  
  
     [!code-vb[#15 VSSDKQuickInfoTest](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&#15;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Реализация поставщика контроллера кратких сведений  
 Поставщик кратких сведений контроллера служит главным образом для экспортировать сама себя в качестве компонента MEF и создать экземпляр контроллера кратких сведений. Так как он является частью компонента MEF, он может импортировать других частей компонента MEF.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Реализация поставщика контроллера кратких сведений  
  
1.  Объявите класс с именем `TestQuickInfoControllerProvider` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.NameAttribute>«Подсказка кратких сведений контроллера» и <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>«текст»:</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>  
  
     [!code-vb[VSSDKQuickInfoTest&16;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&16;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  Импорт <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>как свойство.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>  
  
     [!code-vb[VSSDKQuickInfoTest&17;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&17;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>метода путем создания экземпляра контроллера кратких сведений.</xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>  
  
     [!code-vb[VSSDKQuickInfoTest&18;](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb) ] 
     [!code-cs [VSSDKQuickInfoTest&18;](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы проверить код, создания QuickInfoTest решения и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Для построения и тестирования решений QuickInfoTest  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создайте текстовый файл и введите текст, который содержит слова «добавить» и «вычитание».  
  
4.  Наведите указатель на одно из вхождений «добавить». Подпись и описание `add` метод должен отображаться.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
