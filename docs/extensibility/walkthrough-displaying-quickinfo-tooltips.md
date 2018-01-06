---
title: "Пошаговое руководство: Отображение кратких сведений подсказки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9cd3e9d5e10e6946b4cae8ce02a5a39511e4baaf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Пошаговое руководство: Отображение подсказок кратких сведений
Краткие сведения является функцией IntelliSense, отображающий сигнатуры методов и описания, когда пользователь перемещает указатель на имя метода. Функции, основанный на языке, например кратких сведений можно реализовать путем определения идентификаторов, для которых требуется предоставить описания кратких сведений и создания всплывающей подсказки, в которой для отображения содержимого. Кратких сведений можно определить в контекст языковой службы, можно определить тип имени собственного файла расширения и содержимое и отображение кратких сведений для только этот тип или кратких сведений можно отобразить для существующего типа содержимого (например, «текст»). В этом пошаговом руководстве демонстрируется отображение кратких сведений для типа содержимого «text».  
  
 В примере краткие сведения в этом пошаговом руководстве отображает подсказки при наведении указателя мыши на имени метода. Такой подход требует реализации этих четырех интерфейсов:  
  
-   исходный интерфейс  
  
-   интерфейс поставщика источника  
  
-   интерфейс контроллера  
  
-   интерфейс поставщика контроллера  
  
 Поставщики источника и контроллера, компоненты Managed Extensibility Framework (MEF) и несет ответственность за экспортирование классов источника и контроллера и импорт служб и является посредником например <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, которая создает текст всплывающей подсказки буфер и <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, которое запускает сеанс кратких сведений.  
  
 В этом примере источник кратких сведений использует жестко список метод имена и описания, но в полной реализации языковой службы и документация по языку несут ответственность за предоставление этого содержимого.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
#### <a name="to-create-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалогового окна выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Присвойте решению имя `QuickInfoTest`.  
  
2.  Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создания расширения с помощью шаблона элемента редактор](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
## <a name="implementing-the-quickinfo-source"></a>Реализация источника кратких сведений  
 Краткие сведения источника отвечает за сбор набор идентификаторов и их описания и добавление содержимого в буфер текста всплывающей подсказки при обнаружении один из идентификаторов. В этом примере идентификаторы и их описание только что добавлен в конструктор источника.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Для реализации источника кратких сведений  
  
1.  Добавьте файл класса и назовите его `TestQuickInfoSource`.  
  
2.  Добавьте ссылку на Microsoft.VisualStudio.Language.IntelliSense.  
  
3.  Добавьте следующие операторы imports.  
  
     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  Объявите класс, который реализует <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>и назовите его `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  Добавление полей для кратких сведений поставщика источника, буфер текста и набор метод имена и сигнатуры метода. В этом примере имена и сигнатуры методов инициализируются в `TestQuickInfoSource` конструктора.  
  
     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  Добавьте конструктор, который задает поставщик источника кратких сведений и текстовый буфер и заполняет набор имена методов и подписи методов и описания.  
  
     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. В этом примере метод находит текущего слова или предыдущее слово, если курсор находится в конце строки или буфера текста. Если слово является одним из имен методов, описание для этого имени метода добавляется содержимое кратких сведений.  
  
     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  Также необходимо реализовать метод Dispose(), поскольку <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> реализует <xref:System.IDisposable>:  
  
     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Реализация поставщика источника кратких сведений  
 Поставщик источника кратких сведений служит главным образом для экспортировать сама себя в качестве компонента MEF и создание экземпляра источника кратких сведений. Так как он входит в состав компонентов MEF, он может импортировать других компонентов MEF.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Для реализации поставщика источника кратких сведений  
  
1.  Объявите поставщик кратких сведений с именем `TestQuickInfoSourceProvider` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.NameAttribute> «Источника краткие сведения всплывающей подсказки,» <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> из ранее = «default» и <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «Text».  
  
     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  Импорт две службы редактора <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> и <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, как свойства `TestQuickInfoSourceProvider`.  
  
     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> возвращается новый `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Реализация контроллера кратких сведений  
 Краткие сведения контроллеры определяют, когда должны отображаться краткие сведения. В этом примере кратких сведений отображается, когда указатель находится над слово, которое соответствует одному из имен методов. Краткие сведения о контроллере реализует обработчик событий мыши при наведении указателя мыши, которое запускает сеанс кратких сведений.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Для реализации контроллера кратких сведений  
  
1.  Объявите класс, который реализует <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>и назовите его `TestQuickInfoController`.  
  
     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  Добавьте закрытые поля для представления текста текстовыми буферами, представлены в представление текста, краткие сведения о сеансе и поставщиком контроллера кратких сведений.  
  
     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  Добавьте конструктор, который задает поля и добавляет обработчик события наведения мыши.  
  
     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  Добавьте обработчик событий мыши при наведении указателя мыши, который запускает сеанс кратких сведений.  
  
     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> метода, так что он удаляет обработчик события наведения мыши при отсоединении контроллер из текстового представления.  
  
     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> метод и <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> метод как пустые методы для этого примера.  
  
     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Реализация поставщика контроллера кратких сведений  
 Поставщик кратких сведений контроллера служит главным образом для экспортировать сама себя в качестве компонента MEF и создание экземпляра контроллера кратких сведений. Так как он входит в состав компонентов MEF, он может импортировать других компонентов MEF.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Для реализации поставщика контроллера кратких сведений  
  
1.  Объявите класс с именем `TestQuickInfoControllerProvider` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.NameAttribute> «Контроллера подсказки краткие сведения» и <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «Text»:  
  
     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  Импорт <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> как свойство.  
  
     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> метод путем создания экземпляра контроллера кратких сведений.  
  
     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы проверить код, выполните сборку решения QuickInfoTest и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Для построения и тестирования решения QuickInfoTest  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создайте текстовый файл тип текст, который содержит слова «добавить» и «вычитание».  
  
4.  Наведите указатель мыши на одно из вхождений «добавить». Подпись и описание `add` метода должны отображаться.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)