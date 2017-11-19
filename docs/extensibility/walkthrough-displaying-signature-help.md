---
title: "Пошаговое руководство: Отображение справки сигнатуры | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7078ee1e125ca11b0707b22b0d824cd0fc2d75b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-displaying-signature-help"></a>Пошаговое руководство: Отображение справки сигнатуры
Справка по сигнатурам (также известный как *сведения о параметре*) отображает подписи метода во всплывающей подсказке, когда пользователь вводит символ начала списка параметра (обычно открывающая скобка). Как параметр и параметр разделителя (обычно запятую) типизированы, подсказка обновляется для отображения следующего параметра полужирным шрифтом. Справка по сигнатурам можно определить в контекст языковой службы, можно определить тип имени собственного файла расширения и содержимое и отобразить справку по подписи для только этот тип или можно отобразить справку по подписи для существующего типа содержимого (например, «текст»). В этом пошаговом руководстве показано, как отобразить справку по подписи для типа содержимого «text».  
  
 Справка по сигнатурам обычно запускается, введя определенный символ, например, "(" (открывающая скобка) и закрывается, введя другой символ, например, «)» (закрывающая круглая скобка). Возможности IntelliSense, которые вызываются, введя символ может быть реализован с помощью обработчика команд для нажатий клавиш ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса) и поставщика обработчик, который реализует <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> интерфейса. Чтобы создать источник Справка по сигнатурам, который представляет собой список подписей, участвующих в Справка по сигнатурам, реализовать <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> интерфейс и поставщик, реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> интерфейса. Поставщики, компоненты Managed Extensibility Framework (MEF) и несет ответственность за экспортирование классов источника и контроллера и импорта служб и брокеры, например, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, который позволяет перейти в буфер текста и <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, которое запускает сеанс справки сигнатуры.  
  
 В этом пошаговом руководстве показано, как реализовать Справка по сигнатурам для жестко набор идентификаторов. В полной реализации языка отвечает за предоставление этого содержимого.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
#### <a name="to-create-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалогового окна выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Присвойте решению имя `SignatureHelpTest`.  
  
2.  Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создания расширения с помощью шаблона элемента редактор](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
4.  Добавьте следующие ссылки в проект и убедитесь, что **CopyLocal** равно `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Реализация подписи сигнатуры и параметры  
 Справка по сигнатурам источник основана на подписей, которые реализуют <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, каждый из которых содержит параметры, которые реализуют <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. В полную реализацию эти данные будут получить в документацию по языку, но в этом примере подписи являются фиксированными.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Для реализации Справка по сигнатурам сигнатуры и параметры  
  
1.  Добавьте файл класса и назовите его `SignatureHelpSource`.  
  
2.  Добавьте следующие операторы imports.  
  
     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]  
  
3.  Добавьте класс с именем `TestParameter` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]  
  
4.  Добавьте конструктор, который задает все свойства.  
  
     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]  
  
5.  Добавление свойства <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]  
  
6.  Добавьте класс с именем `TestSignature` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]  
  
7.  Добавьте несколько закрытых полей.  
  
     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]  
  
8.  Добавьте конструктор, который задает поля и подписывается на <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> событий.  
  
     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]  
  
9. Объявите `CurrentParameterChanged` событий. Это событие возникает, когда пользователь заполняет один из параметров в сигнатуре.  
  
     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]  
  
10. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> свойство, чтобы он вызывает `CurrentParameterChanged` событие при изменении значения свойства.  
  
     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]  
  
11. Добавьте метод, который вызывает `CurrentParameterChanged` событий.  
  
     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]  
  
12. Добавьте метод, который вычисляет параметр текущего числа запятые в <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> числу запятые в сигнатуре.  
  
     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]  
  
13. Добавьте обработчик событий для <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> событие, которое вызывает `ComputeCurrentParameter()` метод.  
  
     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]  
  
14. Реализуйте свойство <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Это свойство содержит <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , соответствующий диапазон текста в буфере, к которому применяется подпись.  
  
     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]  
  
15. Реализуйте другие параметры.  
  
     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]  
  
## <a name="implementing-the-signature-help-source"></a>Реализация источника справки подписи  
 Справка по сигнатурам источник — это набор подписей, для которых необходимо указать сведения.  
  
#### <a name="to-implement-the-signature-help-source"></a>Для реализации источника Справка по сигнатурам  
  
1.  Добавьте класс с именем `TestSignatureHelpSource` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]  
  
2.  Добавьте ссылку на буфер текста.  
  
     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]  
  
3.  Добавьте конструктор, который задает буфер текста и Справка по сигнатурам поставщик источника.  
  
     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]  
  
4.  Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. В этом примере подписи являются фиксированными, однако в полной реализации было бы получить эти сведения от документация по языку.  
  
     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]  
  
5.  Вспомогательный метод `CreateSignature()` предоставляется только для иллюстрации.  
  
     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]  
  
6.  Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. В этом примере существует только два подписи, каждый из которых имеет два параметра. Таким образом этот метод не требуется. В полное реализации, в которой доступно больше одного источника, Справка по сигнатурам, этот метод используется, следует ли источник Справка по сигнатурам наивысший приоритет может предоставить соответствующей сигнатурой. Если это невозможно, метод возвращает значение null и далее наивысшим приоритетом источника выдается запрос на ввод совпадения.  
  
     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]  
  
7.  Реализуйте метод Dispose():  
  
     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Реализация поставщика источника подписи справки  
 Справка по сигнатурам поставщик источника отвечает для экспорта части компонента Managed Extensibility Framework (MEF), а также для создания экземпляра источника Справка по сигнатурам.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Для реализации поставщика источника Справка по сигнатурам  
  
1.  Добавьте класс с именем `TestSignatureHelpSourceProvider` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текст» и <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> из ранее = «default».  
  
     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]  
  
2.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> путем создания экземпляра `TestSignatureHelpSource`.  
  
     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]  
  
## <a name="implementing-the-command-handler"></a>Реализация обработчика команд  
 Справка по сигнатурам обычно инициируется (символьных и отключенные по) символов. Можно обработать эти нажатия клавиш, реализовав <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , чтобы оно запускалось Справка по сигнатурам сеанса, когда он получает (знака предшествует имени метода известные и закрывает сеанс, когда он получает) символов.  
  
#### <a name="to-implement-the-command-handler"></a>Для реализации обработчика команд  
  
1.  Добавьте класс с именем `TestSignatureHelpCommand` , реализующий <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]  
  
2.  Добавьте закрытые поля для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> (который позволяет добавить обработчик команд в цепочке управления обработчики) адаптера, представления текста, Справка по сигнатурам брокера и сеанса, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, а затем <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]  
  
3.  Добавьте конструктор для инициализации этих полей и для добавления фильтра команда цепочке управления фильтры.  
  
     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]  
  
4.  Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод для запуска сеанса Справка по сигнатурам, когда фильтр команда получает (символ после одного из имен известных методов и закрыть сеанс, когда он получает) символов во время сеанса все еще активны. В каждом случае перенаправляется команда.  
  
     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]  
  
5.  Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод, чтобы он всегда отправляет команду.  
  
     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Реализация поставщика команду справки подписи  
 Справка по сигнатурам команды можно предоставить путем реализации <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> для создания экземпляра обработчик команд, при создании представления текста.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Для реализации поставщика Справка по сигнатурам команды  
  
1.  Добавьте класс с именем `TestSignatureHelpController` , реализующий <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, и <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]  
  
2.  Импорт <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (используется для получения <xref:Microsoft.VisualStudio.Text.Editor.ITextView>с учетом <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объекта), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (используется для поиска текущего слова) и <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (для запуска сеанса Справка по сигнатурам).  
  
     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]  
  
3.  Реализуйте <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> метод путем создания экземпляра `TestSignatureCommandHandler`.  
  
     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы проверить код, выполните сборку решения SignatureHelpTest и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Для построения и тестирования решения SignatureHelpTest  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создайте текстовый файл и тип, текст, который содержит слово «добавить», а также открывающую скобку.  
  
4.  После ввода открывающей скобки, вы увидите всплывающую подсказку, которая отображает список две подписи для `add()` метод.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)