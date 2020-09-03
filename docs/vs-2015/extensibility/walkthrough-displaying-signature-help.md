---
title: Пошаговое руководство. Отображение справки по сигнатурам | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202051"
---
# <a name="walkthrough-displaying-signature-help"></a>Пошаговое руководство. Отображение справки сигнатуры
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Справка по сигнатурам (также называемая *сведениями о параметрах*) отображает сигнатуру метода в подсказке, когда пользователь вводит начальный символ списка параметров (обычно это открывающая круглая скобка). При вводе разделителя параметров и параметров (обычно запятая) подсказка обновляется для отображения следующего параметра полужирным шрифтом. Вы можете определить справку по сигнатуре в контексте языковой службы или определить собственное расширение имени файла и тип содержимого, а также отобразить справку по сигнатуре для этого типа, или же можно отобразить справку по сигнатуре для существующего типа содержимого (например, "Text"). В этом пошаговом руководстве показано, как отобразить справку по сигнатуре для типа содержимого text.  
  
 Справка по сигнатуре обычно запускается путем ввода определенного символа, например "(" (открывающая скобка), и закрытия путем ввода другого символа, например ")" (закрывающей скобки). Функции IntelliSense, активируемые при вводе символа, могут быть реализованы с помощью обработчика команд для нажатий клавиш ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс) и поставщика обработчика, реализующего <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> интерфейс. Для создания источника справки сигнатур, который является списком подписей, участвующих в справке по сигнатурам, реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> интерфейс и поставщик источника, который реализует <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> интерфейс. Поставщики — это компоненты компонентов Managed Extensibility Framework (MEF), которые отвечают за экспорт классов источников и контроллеров, а также импорт служб и брокеров, например <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> ,, который позволяет перемещаться по текстовому буферу и <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> , который активирует сеанс справки сигнатуры.  
  
 В этом пошаговом руководстве показано, как реализовать справку по сигнатурам для жестко запрограммированного набора идентификаторов. В полной реализации язык отвечает за предоставление этого содержимого.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
#### <a name="to-create-a-mef-project"></a>Создание проекта MEF  
  
1. Создание проекта VSIX C#. (В диалоговом окне **Новый проект** выберите **Visual C#/Extensibility**, а затем **проект VSIX**.) Присвойте решению имя `SignatureHelpTest` .  
  
2. Добавьте шаблон элемента классификатора редактора в проект. Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Удалите файлы существующих классов.  
  
4. Добавьте в проект следующие ссылки и убедитесь, что для свойства **CopyLocal** задано значение `false` :  
  
     Microsoft. VisualStudio. Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft. VisualStudio. OLE. Interop  
  
     Microsoft. VisualStudio. Shell.,  
  
     Microsoft. VisualStudio. TextManager. Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Реализация сигнатур и параметров справки  
 Источник справки по сигнатуре основан на сигнатурах, реализующих <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> , каждый из которых содержит параметры, реализующие <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> . В полной реализации эта информация будет получена из документации по языку, но в этом примере сигнатуры жестко запрограммированы.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Реализация сигнатур и параметров в справке по сигнатурам  
  
1. Добавьте файл класса с именем `SignatureHelpSource`.  
  
2. Добавьте приведенные ниже импортированные данные.  
  
     [!code-csharp[VSSDKSignatureHelpTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#1)]
     [!code-vb[VSSDKSignatureHelpTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#1)]  
  
3. Добавьте класс с именем `TestParameter` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#2)]
     [!code-vb[VSSDKSignatureHelpTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#2)]  
  
4. Добавьте конструктор, который задает все свойства.  
  
     [!code-csharp[VSSDKSignatureHelpTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#3)]
     [!code-vb[VSSDKSignatureHelpTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#3)]  
  
5. Добавьте свойства <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#4)]
     [!code-vb[VSSDKSignatureHelpTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#4)]  
  
6. Добавьте класс с именем `TestSignature` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#5)]
     [!code-vb[VSSDKSignatureHelpTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#5)]  
  
7. Добавьте некоторые закрытые поля.  
  
     [!code-csharp[VSSDKSignatureHelpTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#6)]
     [!code-vb[VSSDKSignatureHelpTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#6)]  
  
8. Добавьте конструктор, который задает поля и подписывается на <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> событие.  
  
     [!code-csharp[VSSDKSignatureHelpTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#7)]
     [!code-vb[VSSDKSignatureHelpTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#7)]  
  
9. Объявите `CurrentParameterChanged` событие. Это событие возникает при заполнении пользователем одного из параметров в сигнатуре.  
  
     [!code-csharp[VSSDKSignatureHelpTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#8)]
     [!code-vb[VSSDKSignatureHelpTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#8)]  
  
10. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> свойство таким образом, чтобы оно вызывало `CurrentParameterChanged` событие при изменении значения свойства.  
  
     [!code-csharp[VSSDKSignatureHelpTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#9)]
     [!code-vb[VSSDKSignatureHelpTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#9)]  
  
11. Добавьте метод, который вызывает `CurrentParameterChanged` событие.  
  
     [!code-csharp[VSSDKSignatureHelpTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#10)]
     [!code-vb[VSSDKSignatureHelpTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#10)]  
  
12. Добавьте метод, который выполняет вычисление текущего параметра, сравнивая количество запятый в <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> с числом запятых в сигнатуре.  
  
     [!code-csharp[VSSDKSignatureHelpTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#11)]
     [!code-vb[VSSDKSignatureHelpTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#11)]  
  
13. Добавьте обработчик событий для <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> события, вызывающего `ComputeCurrentParameter()` метод.  
  
     [!code-csharp[VSSDKSignatureHelpTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#12)]
     [!code-vb[VSSDKSignatureHelpTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#12)]  
  
14. Реализуйте свойство <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Это свойство содержит объект <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , соответствующий диапазону текста в буфере, к которому применяется подпись.  
  
     [!code-csharp[VSSDKSignatureHelpTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#13)]
     [!code-vb[VSSDKSignatureHelpTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#13)]  
  
15. Реализуйте другие параметры.  
  
     [!code-csharp[VSSDKSignatureHelpTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#14)]
     [!code-vb[VSSDKSignatureHelpTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#14)]  
  
## <a name="implementing-the-signature-help-source"></a>Реализация источника справки по сигнатурам  
 Источник справки по подписи — это набор сигнатур, для которых предоставляются сведения.  
  
#### <a name="to-implement-the-signature-help-source"></a>Реализация источника справки по сигнатурам  
  
1. Добавьте класс с именем `TestSignatureHelpSource` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#15)]
     [!code-vb[VSSDKSignatureHelpTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#15)]  
  
2. Добавьте ссылку на текстовый буфер.  
  
     [!code-csharp[VSSDKSignatureHelpTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#16)]
     [!code-vb[VSSDKSignatureHelpTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#16)]  
  
3. Добавьте конструктор, который задает текстовый буфер и поставщик источника справки по сигнатурам.  
  
     [!code-csharp[VSSDKSignatureHelpTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#17)]
     [!code-vb[VSSDKSignatureHelpTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#17)]  
  
4. Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. В этом примере сигнатуры жестко запрограммированы, но в полной реализации эти сведения можно получить из документации по языку.  
  
     [!code-csharp[VSSDKSignatureHelpTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#18)]
     [!code-vb[VSSDKSignatureHelpTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#18)]  
  
5. Вспомогательный метод `CreateSignature()` предоставляется только для иллюстрации.  
  
     [!code-csharp[VSSDKSignatureHelpTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#19)]
     [!code-vb[VSSDKSignatureHelpTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#19)]  
  
6. Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. В этом примере есть только две сигнатуры, каждая из которых имеет два параметра. Поэтому этот метод не является обязательным. В более новой реализации, в которой доступно несколько источников справки сигнатур, этот метод используется для определения того, может ли источник справки сигнатуры с наивысшим приоритетом предоставлять соответствующую сигнатуру. Если это невозможно, метод возвращает значение null, и источнику, имеющему следующий приоритет, будет предложено указать соответствие.  
  
     [!code-csharp[VSSDKSignatureHelpTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#20)]
     [!code-vb[VSSDKSignatureHelpTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#20)]  
  
7. Реализуйте метод Dispose ():  
  
     [!code-csharp[VSSDKSignatureHelpTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#21)]
     [!code-vb[VSSDKSignatureHelpTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#21)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Реализация поставщика источника справки по сигнатурам  
 Поставщик источника справки по подписи отвечает за экспорт части компонента Managed Extensibility Framework (MEF) и создание экземпляра справки по сигнатурам.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Реализация поставщика источника справки по сигнатурам  
  
1. Добавьте класс с именем, `TestSignatureHelpSourceProvider` реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> , и экспортируйте его с помощью <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , типа <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" и объекта <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Before = "default".  
  
     [!code-csharp[VSSDKSignatureHelpTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#22)]
     [!code-vb[VSSDKSignatureHelpTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#22)]  
  
2. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> , создав экземпляр `TestSignatureHelpSource` .  
  
     [!code-csharp[VSSDKSignatureHelpTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#23)]
     [!code-vb[VSSDKSignatureHelpTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#23)]  
  
## <a name="implementing-the-command-handler"></a>Реализация обработчика команд  
 Справка по сигнатуре обычно активируется символом (символом и закрывается). Эти нажатия клавиш можно обменять, реализуя, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> чтобы при получении символа, которому предшествует известное имя метода, запустился символ (перед ним закрывается).  
  
#### <a name="to-implement-the-command-handler"></a>Реализация обработчика команд  
  
1. Добавьте класс с именем `TestSignatureHelpCommand` , реализующий <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#24)]
     [!code-vb[VSSDKSignatureHelpTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#24)]  
  
2. Добавьте частные поля для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> адаптера (который позволяет добавить обработчик команд в цепочку обработчиков команд), представление текста, брокер справки и сеанс, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> а также следующий объект <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#25)]
     [!code-vb[VSSDKSignatureHelpTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#25)]  
  
3. Добавьте конструктор для инициализации этих полей и добавьте фильтр команд в цепочку фильтров команд.  
  
     [!code-csharp[VSSDKSignatureHelpTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#26)]
     [!code-vb[VSSDKSignatureHelpTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#26)]  
  
4. Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод для активации сеанса справки по сигнатурам, когда фильтр команд получает символ (символ после одного из известных имен методов, а также для закрытия сеанса при получении символа), пока сеанс остается активным. Во всех случаях команда пересылается.  
  
     [!code-csharp[VSSDKSignatureHelpTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#27)]
     [!code-vb[VSSDKSignatureHelpTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#27)]  
  
5. Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод таким образом, чтобы он всегда направлял команду.  
  
     [!code-csharp[VSSDKSignatureHelpTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#28)]
     [!code-vb[VSSDKSignatureHelpTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#28)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Реализация поставщика команд справки по сигнатурам  
 Можно предоставить команду справки сигнатуры, реализовав <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> для создания экземпляра обработчика команд при создании текстового представления.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Реализация поставщика команды справки по сигнатуре  
  
1. Добавьте класс с именем `TestSignatureHelpController` , реализующий <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> и экспортирующий его с помощью <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> и <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#29)]
     [!code-vb[VSSDKSignatureHelpTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#29)]  
  
2. Импортируйте объект <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (используемый для получения <xref:Microsoft.VisualStudio.Text.Editor.ITextView> объекта, задавая <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объект), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (используемый для поиска текущего слова) и <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (для активации сеанса справки сигнатуры).  
  
     [!code-csharp[VSSDKSignatureHelpTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#30)]
     [!code-vb[VSSDKSignatureHelpTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#30)]  
  
3. Реализуйте <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> метод, создав экземпляр `TestSignatureCommandHandler` .  
  
     [!code-csharp[VSSDKSignatureHelpTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#31)]
     [!code-vb[VSSDKSignatureHelpTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#31)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы протестировать этот код, создайте решение Сигнатурехелптест и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Создание и тестирование решения Сигнатурехелптест  
  
1. Создайте решение.  
  
2. При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3. Создайте текстовый файл и введите текст, содержащий слово "Добавить", и открывающую круглую скобку.  
  
4. После ввода открывающей скобки вы увидите подсказку, которая отображает список двух сигнатур для `add()` метода.  
  
## <a name="see-also"></a>См. также:  
 [Пошаговое руководство. Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
