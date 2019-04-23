---
title: Пошаговое руководство. Отображение справки сигнатуры | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 280b5b517089ad9e5b38cb00dc9b14c68253d1e6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108169"
---
# <a name="walkthrough-displaying-signature-help"></a>Пошаговое руководство. Отображение справки по цифровым подписям
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Справка по сигнатурам (также известный как *сведения о параметрах*) отображается подпись метода во всплывающей подсказке, когда пользователь вводит символ начала списка параметра (обычно открывающая скобка). Как параметр и параметр разделитель (обычно запятой) типизированы, подсказка обновляется для отображения следующего параметра полужирным шрифтом. Справка по сигнатурам можно определить в контексте службы языка, можно определить тип имени собственного файла расширения и содержимого и отображения справки сигнатуры для только этого типа или для существующих типов (например, «text») можно отобразить Справка по сигнатурам. В этом пошаговом руководстве показано, как для отображения справки сигнатуры для типа содержимого «text».  
  
 Справка по сигнатурам обычно запускается, введя определенный символ, например, "(" (открывающая скобка), а закрыто, введя другой символ, например, «)» (закрывающая круглая скобка). Возможности IntelliSense, которые запускаются, введя символ может быть реализован с помощью обработчика команды клавиш ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс) и поставщика обработчик, который реализует <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> интерфейс. Чтобы создать источник Справка по сигнатурам, который является списком подписей, которые участвуют в Справка по сигнатурам, реализовать <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> интерфейс и поставщика источника, который реализует <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> интерфейс. Какие поставщики являются составные части Managed Extensibility Framework (MEF) и несете ответственность за экспортирование классов источника и контроллера и импорта служб и брокеров, например, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, который позволяет перейти в текстовом буфере и <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, который запускает сеанс справки сигнатуры.  
  
 В этом пошаговом руководстве показано, как реализовать Справка по сигнатурам для жестко набор идентификаторов. В полной реализации языка отвечает за предоставление этого содержимого.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
#### <a name="to-create-a-mef-project"></a>Создание проекта MEF  
  
1. Создайте проект VSIX C#. (В **новый проект** диалоговом окне выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Назовите решение `SignatureHelpTest`.  
  
2. Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Удалите файлы существующих классов.  
  
4. Добавьте следующие ссылки в проект и убедитесь, что **CopyLocal** присваивается `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Реализация подпись справка сигнатуры и параметры  
 Справка по сигнатурам источник основана на подписей, которые реализуют <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, каждый из которых содержит параметры, которые реализуют <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. В полную реализацию эти сведения будут получены из документации по языку, но в этом примере сигнатуры жестко запрограммированы.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Для реализации Справка по сигнатурам сигнатуры и параметры  
  
1. Добавьте файл класса с именем `SignatureHelpSource`.  
  
2. Добавьте следующие импорты.  
  
     [!code-csharp[VSSDKSignatureHelpTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#1)]
     [!code-vb[VSSDKSignatureHelpTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#1)]  
  
3. Добавьте класс с именем `TestParameter` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#2)]
     [!code-vb[VSSDKSignatureHelpTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#2)]  
  
4. Добавьте конструктор, который задает всем свойствам.  
  
     [!code-csharp[VSSDKSignatureHelpTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#3)]
     [!code-vb[VSSDKSignatureHelpTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#3)]  
  
5. Добавление свойства <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#4)]
     [!code-vb[VSSDKSignatureHelpTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#4)]  
  
6. Добавьте класс с именем `TestSignature` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#5)]
     [!code-vb[VSSDKSignatureHelpTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#5)]  
  
7. Добавьте несколько закрытых полей.  
  
     [!code-csharp[VSSDKSignatureHelpTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#6)]
     [!code-vb[VSSDKSignatureHelpTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#6)]  
  
8. Добавьте конструктор, который задает поля и подписывается на <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> событий.  
  
     [!code-csharp[VSSDKSignatureHelpTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#7)]
     [!code-vb[VSSDKSignatureHelpTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#7)]  
  
9. Объявите `CurrentParameterChanged` событий. Это событие возникает, когда пользователь заполняет один из параметров в сигнатуре.  
  
     [!code-csharp[VSSDKSignatureHelpTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#8)]
     [!code-vb[VSSDKSignatureHelpTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#8)]  
  
10. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> свойство, так что он вызывает `CurrentParameterChanged` событие при изменении значения свойства.  
  
     [!code-csharp[VSSDKSignatureHelpTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#9)]
     [!code-vb[VSSDKSignatureHelpTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#9)]  
  
11. Добавьте метод, который вызывает `CurrentParameterChanged` событий.  
  
     [!code-csharp[VSSDKSignatureHelpTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#10)]
     [!code-vb[VSSDKSignatureHelpTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#10)]  
  
12. Добавьте метод, вычисляющий текущий параметр числа запятых в <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> число запятых в сигнатуре.  
  
     [!code-csharp[VSSDKSignatureHelpTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#11)]
     [!code-vb[VSSDKSignatureHelpTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#11)]  
  
13. Добавьте обработчик событий для <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> событие, которое вызывает `ComputeCurrentParameter()` метод.  
  
     [!code-csharp[VSSDKSignatureHelpTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#12)]
     [!code-vb[VSSDKSignatureHelpTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#12)]  
  
14. Реализуйте свойство <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Это свойство содержит <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , соответствующий диапазон текста в буфере, к которому относится подпись.  
  
     [!code-csharp[VSSDKSignatureHelpTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#13)]
     [!code-vb[VSSDKSignatureHelpTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#13)]  
  
15. Реализуйте другие параметры.  
  
     [!code-csharp[VSSDKSignatureHelpTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#14)]
     [!code-vb[VSSDKSignatureHelpTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#14)]  
  
## <a name="implementing-the-signature-help-source"></a>Реализация источника справки сигнатуры  
 Справка по сигнатурам источником является набор сигнатур, для которых необходимо указать сведения.  
  
#### <a name="to-implement-the-signature-help-source"></a>Для реализации источника Справка по сигнатурам  
  
1. Добавьте класс с именем `TestSignatureHelpSource` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#15)]
     [!code-vb[VSSDKSignatureHelpTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#15)]  
  
2. Добавьте ссылку на текстовый буфер.  
  
     [!code-csharp[VSSDKSignatureHelpTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#16)]
     [!code-vb[VSSDKSignatureHelpTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#16)]  
  
3. Добавьте конструктор, который задает текстовый буфер и Справка по сигнатурам поставщик источника.  
  
     [!code-csharp[VSSDKSignatureHelpTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#17)]
     [!code-vb[VSSDKSignatureHelpTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#17)]  
  
4. Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. В этом примере жестко запрограммированы сигнатуры, но в полной реализации бы получить эти сведения из документации по языку.  
  
     [!code-csharp[VSSDKSignatureHelpTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#18)]
     [!code-vb[VSSDKSignatureHelpTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#18)]  
  
5. Вспомогательный метод `CreateSignature()` предоставляется только для справки.  
  
     [!code-csharp[VSSDKSignatureHelpTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#19)]
     [!code-vb[VSSDKSignatureHelpTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#19)]  
  
6. Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. В этом примере есть только две подписи, каждый из которых имеет два параметра. Таким образом этот метод не требуется. В более полной реализации, в котором доступно больше одного источника, Справка по сигнатурам, этот метод используется, следует ли источник Справка по сигнатурам с наивысшим приоритетом может предоставить соответствующей сигнатурой. Если это невозможно, метод возвращает значение null, и Далее-с наивысшим приоритетом источника предлагается ввести совпадение.  
  
     [!code-csharp[VSSDKSignatureHelpTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#20)]
     [!code-vb[VSSDKSignatureHelpTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#20)]  
  
7. Реализуйте метод Dispose():  
  
     [!code-csharp[VSSDKSignatureHelpTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#21)]
     [!code-vb[VSSDKSignatureHelpTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#21)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Реализация поставщика источника справки сигнатуры  
 Справка по сигнатурам поставщик источника отвечает для экспорта части компонента Managed Extensibility Framework (MEF), а также для создания экземпляра источника Справка по сигнатурам.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Реализация поставщика источника Справка по сигнатурам  
  
1. Добавьте класс с именем `TestSignatureHelpSourceProvider` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текст» и <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> из Before = «default».  
  
     [!code-csharp[VSSDKSignatureHelpTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#22)]
     [!code-vb[VSSDKSignatureHelpTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#22)]  
  
2. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> путем создания экземпляра `TestSignatureHelpSource`.  
  
     [!code-csharp[VSSDKSignatureHelpTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#23)]
     [!code-vb[VSSDKSignatureHelpTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#23)]  
  
## <a name="implementing-the-command-handler"></a>Реализация обработчика команд  
 Справка по сигнатурам обычно инициируется (символьных и отклоненные по) символов. Можно обрабатывать эти нажатия клавиш, реализовав <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> таким образом, чтобы она инициирует сеанс справки сигнатуры, при получении (символ предшествует имени метода известных и закрывает сеанс, когда он получает) символов.  
  
#### <a name="to-implement-the-command-handler"></a>Чтобы реализовать обработчик команд  
  
1. Добавьте класс с именем `TestSignatureHelpCommand` , реализующий <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#24)]
     [!code-vb[VSSDKSignatureHelpTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#24)]  
  
2. Добавьте закрытые поля для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> адаптера (который служит для добавления обработчика команды с обработчиками команд цепочки), представление текста, Справка по сигнатурам брокера и сеанса, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, а следующие <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#25)]
     [!code-vb[VSSDKSignatureHelpTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#25)]  
  
3. Добавьте конструктор, чтобы инициализировать эти поля и добавить фильтр команд к цепочке фильтров команд.  
  
     [!code-csharp[VSSDKSignatureHelpTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#26)]
     [!code-vb[VSSDKSignatureHelpTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#26)]  
  
4. Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод для запуска сеанса Справка по сигнатурам, когда получает фильтр команды (символ после одно из имен известных методов и для закрытия сеанса, при получении) символов во время сеанса по-прежнему активна. В каждом случае перенаправляется команда.  
  
     [!code-csharp[VSSDKSignatureHelpTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#27)]
     [!code-vb[VSSDKSignatureHelpTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#27)]  
  
5. Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод, чтобы он всегда перенаправляет команды.  
  
     [!code-csharp[VSSDKSignatureHelpTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#28)]
     [!code-vb[VSSDKSignatureHelpTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#28)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Реализация поставщика команду справки сигнатуры  
 Можно указать команду Справка по сигнатурам, реализовав <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> для создания экземпляра обработчика команды при создании представления текста.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Реализация поставщика команды Справка по сигнатурам  
  
1. Добавьте класс с именем `TestSignatureHelpController` , реализующий <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, и <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#29)]
     [!code-vb[VSSDKSignatureHelpTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#29)]  
  
2. Импорт <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (используется для получения <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, присвоенный <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объекта), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (используется для поиска текущего слова) и <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (для запуска сеанса справки сигнатуры).  
  
     [!code-csharp[VSSDKSignatureHelpTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#30)]
     [!code-vb[VSSDKSignatureHelpTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#30)]  
  
3. Реализуйте <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> метод путем создания экземпляра `TestSignatureCommandHandler`.  
  
     [!code-csharp[VSSDKSignatureHelpTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#31)]
     [!code-vb[VSSDKSignatureHelpTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#31)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы протестировать этот код, выполните сборку решения SignatureHelpTest и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Построение и тестирование решения SignatureHelpTest  
  
1. Постройте решение.  
  
2. При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3. Создайте текстовый файл и введите текст, который включает слово «добавить», а также открывающую скобку.  
  
4. После открывающей скобки, вы увидите подсказку, которая отображает список две подписи для `add()` метод.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
