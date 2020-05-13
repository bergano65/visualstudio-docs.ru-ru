---
title: 'Пошаговая прогулка: Отображение Справки по подписи (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f85d7eb3959064468e7583ec0c8a927f3e139daf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697421"
---
# <a name="walkthrough-display-signature-help"></a>Пошаговая прогулка: Помощь в отображении подписи
Справка о подписи (также известная как *Параметр Информация)* отображает подпись метода в наборе инструментов, когда пользователь набирает стартовый символ списка параметров (обычно открываюшую скобку). По мере набранного параметра и параметра (обычно запятой) набор инструментов обновляется, чтобы показать следующий параметр жирным шрифтом. Вы можете определить справку о подписи следующим образом: в контексте языковой службы определить свое собственное расширение и тип содержимого и отобразить справку о подписи только для этого типа, или отобразить справку о подписи для существующего типа содержимого (например, "текст"). В этом пошаговом показании, как отобразить справку о подписи для типа содержимого "текст".

 Справка о подписи обычно вызывается путем ввода определенного символа, например, "(" (открытие скобки) и отклонена путем ввода другого символа, например,") "(закрытие скобки). Функции IntelliSense, срабатывающие при вводе персонажа, могут быть реализованы с помощью обработчика команд для нажатий клавиш <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> (интерфейс) и поставщика обработчиков, который реализует <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> интерфейс. Для создания источника справки подписи, который представляет собой список <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> подписей, участвующих <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> в справке подписи, реализуйте интерфейс и поставщик исходных данных, который запускает интерфейс. Поставщики являются компонентами управляемой расширительности (MEF) и отвечают за экспорт классов исходного кода и контроллера и импорт услуг и брокеров, например, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, который позволяет перемещаться в буфере текста, и <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, который запускает сеанс справки подписи.

 В этом пошаговом показании, как настроить справку о подписях для жестко закодированного набора идентификаторов. В полной реализации, язык несет ответственность за предоставление этого содержания.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="creating-a-mef-project"></a>Создание проекта MEF

#### <a name="to-create-a-mef-project"></a>Создание проекта MEF

1. Создайте проект СЗ VSIX. (В **диалоге нового проекта** выберите **Visual C / Расширяемость,** затем **VSIX Project**.) Назовите решение. `SignatureHelpTest`

2. Добавьте шаблон элемента классификатора редактора в проект. Для получения дополнительной информации [см. Создать расширение с шаблоном элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

4. Добавьте следующие ссылки на проект и убедитесь, что **CopyLocal** настроен на: `false`

     Microsoft.VisualStudio.Редактор

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.14.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Реализация подписи и параметры справки подписи
 Источник справки подписи основан <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>на сигнатурах, <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>которые реализуем, каждый из которых содержит параметры, которые реализуем. При полной реализации эта информация будет получена из языковой документации, но в этом примере подписи жестко закодированы.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Реализация подписей и параметров справки подписи

1. Добавьте файл класса с именем `SignatureHelpSource`.

2. Добавьте приведенные ниже импортированные данные.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. Добавьте класс, названный, `TestParameter` который <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>реализуется.

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. Добавьте конструктор, который устанавливает все свойства.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. Добавить свойства <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. Добавьте класс, названный, `TestSignature` который <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>реализуется.

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. Добавьте несколько частных полей.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. Добавьте конструктор, который устанавливает поля и <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> подписывается на событие.

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Объявить `CurrentParameterChanged` событие. Это событие возникает, когда пользователь заполняет один из параметров в подписи.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> свойства, чтобы оно `CurrentParameterChanged` выражалось при изменении значения свойства.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. Добавьте метод, `CurrentParameterChanged` который поднимает событие.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. Добавьте метод, который вычисляет текущий параметр, сравнивая количество запятых в <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> количестве запятых в подписи.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Добавьте обработчик <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> события для `ComputeCurrentParameter()` события, который вызывает метод.

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Реализуйте свойство <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Это свойство <xref:Microsoft.VisualStudio.Text.ITrackingSpan> содержит, что соответствует пролету текста в буфере, к которому применяется подпись.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Реализация других параметров.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>Реализация источника справки подписи
 Источник справки подписи — это набор подписей, для которых вы предоставляете информацию.

#### <a name="to-implement-the-signature-help-source"></a>Реализация источника справки подписи

1. Добавьте класс, названный, `TestSignatureHelpSource` который <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>реализуется.

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. Добавьте ссылку на текстовый буфер.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. Добавьте конструктор, который устанавливает буфер текста, и поставщик источников справки подписи.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. В этом примере подписи жестко закодированы, но при полной реализации эту информацию можно получить из языковой документации.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. Метод помощника `CreateSignature()` предоставляется только для иллюстрации.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. В этом примере есть только две подписи, каждая из которых имеет два параметра. Поэтому этот метод не требуется. В более полной реализации, в которой доступно более одного источника справки подписи, этот метод используется для определения того, может ли наивысший приоритет источника справки подписи предоставить соответствующую подпись. Если это невозможно, метод возвращается недействительным, и следующему приоритету source предлагается предоставить совпадение.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. Реализация `Dispose()` метода:

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>Реализация поставщика источников справки подписи
 Поставщик источника справки подписи отвечает за экспорт компонента Управляемой расширительности (MEF) и за мгновенное воспроизведение источника Справки подписи.

#### <a name="to-implement-the-signature-help-source-provider"></a>Реализация поставщика источников справки подписи

1. `TestSignatureHelpSourceProvider` Добавьте класс, названный, который <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>реализует, и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "текст", и <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> до "по умолчанию".

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> путем мгновенного `TestSignatureHelpSource`.

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Реализация обработчика команд
 Справка подписи обычно вызвана открывающейся скобкой "(" символ омичем и отклонена закрытием скобки") символом. Вы можете обрабатывать эти нажатия <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> клавиш, запуская так, чтобы он запускал сеанс справки подписи, когда он получает символ скобки открытия, предшествующий известному имени метода, и отклоняет сеанс, когда он получает заключительный символ скобки.

#### <a name="to-implement-the-command-handler"></a>Реализация обработчика команд

1. Добавьте класс, названный, `TestSignatureHelpCommand` который <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>реализуется.

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. Добавьте частные <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> поля для адаптера (который позволяет добавлять обработчик команды в цепочку обработчиков команд), текстовое представление, брокер Справка подписи и сеанс, a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, и следующий. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. Добавьте конструктор, чтобы инициализировать эти поля и добавить командный фильтр в цепочку командных фильтров.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. Реализация <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метода для запуска сеанса справки подписи, когда командный фильтр получает начальный скобки "(" символ после одного из известных имен метода, и отклонить сеанс, когда он получает закрывающую скобку ")" символ, пока сеанс все еще активен. В каждом случае команда перенаправляется.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. Реализация <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метода так, чтобы он всегда препровождил команду.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>Реализация поставщика команд-подпрограмм «Справка подписи»
 Вы можете предоставить команду справки <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> подписи, реализовав моменттизировать обработчик команды при создании представления текста.

### <a name="to-implement-the-signature-help-command-provider"></a>Реализация поставщика командных решений Signature Help

1. Добавить класс `TestSignatureHelpController` с <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> именем, который <xref:Microsoft.VisualStudio.Utilities.NameAttribute> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>реализует <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>и экспортирует его с , и .

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. Импортируйте <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (используется для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>получения, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> данного <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> объекта), (используется для поиска <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> текущего слова) и (для запуска сеанса справки подписи).

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. Реализация <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> метода путем мгновенного `TestSignatureCommandHandler`.

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Создайте и протестуйте код
 Чтобы протестировать этот код, создайте решение SignatureHelpTest и запустите его в экспериментальном экземпляре.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Создание и тестирование решения SignatureHelpTest

1. Создайте решение.

2. При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

3. Создайте текстовый файл и введите текст, который включает в себя слово "добавить" плюс открытие скобки.

4. После ввода скобки открытия следует увидеть набор инструментов, который отображает список `add()` из двух подписей для метода.

## <a name="see-also"></a>См. также
- [Прохождение: Свяжите тип содержимого с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
