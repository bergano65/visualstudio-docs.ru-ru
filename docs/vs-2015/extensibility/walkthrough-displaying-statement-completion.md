---
title: Пошаговое руководство. Отображение завершения операторов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db4e63beb1e3d4ff53e547492ae9eae7ee8001e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202011"
---
# <a name="walkthrough-displaying-statement-completion"></a>Пошаговое руководство. Отображение завершения операторов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно реализовать завершение операторов на основе языка, определив идентификаторы, для которых необходимо предоставить завершение, а затем активировать сеанс завершения. Можно определить завершение операторов в контексте языковой службы, определить собственное расширение имени файла и тип содержимого, а затем отобразить завершения только для этого типа, или можно активировать завершение для существующего типа содержимого, например "обычный текст". В этом пошаговом руководстве показано, как активировать завершение операторов для типа содержимого "обычный текст", который является типом содержимого текстовых файлов. Тип содержимого text является предком всех других типов содержимого, включая код и XML-файлы.  
  
 Завершение операторов обычно запускается путем ввода определенных символов (например, при вводе начала идентификатора, например «using»). Обычно он закрывается нажатием клавиши пробел, TAB или Enter для фиксации выделенного фрагмента. Можно реализовать функции IntelliSense, активируемые при вводе символа с помощью обработчика команд для нажатия клавиш ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс) и поставщика обработчика, реализующего <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> интерфейс. Для создания источника завершения, который представляет собой список идентификаторов, участвующих в завершении, реализуют <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> интерфейс и поставщик источника завершения ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> интерфейс). Поставщики являются компонентами компонентов Managed Extensibility Framework (MEF). Они отвечают за экспорт классов источника и контроллера, а также импорт служб и брокеров <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , например,, который позволяет переходить в текстовом буфере, и <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> , который запускает сеанс завершения.  
  
 В этом пошаговом руководстве показано, как реализовать завершение операторов для жестко запрограммированного набора идентификаторов. В полной реализации языковая служба и документация по языку отвечают за предоставление этого содержимого.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
#### <a name="to-create-a-mef-project"></a>Создание проекта MEF  
  
1. Создание проекта VSIX C#. (В диалоговом окне **Новый проект** выберите **Visual C#/Extensibility**, а затем **проект VSIX**.) Присвойте решению имя `CompletionTest` .  
  
2. Добавьте шаблон элемента классификатора редактора в проект. Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Удалите файлы существующих классов.  
  
4. Добавьте в проект следующие ссылки и убедитесь, что для свойства **CopyLocal** задано значение `false` :  
  
     Microsoft. VisualStudio. Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft. VisualStudio. OLE. Interop  
  
     Microsoft. VisualStudio. Shell.,  
  
     Microsoft. VisualStudio. Shell. неизменяемый. 10.0  
  
     Microsoft. VisualStudio. TextManager. Interop  
  
## <a name="implementing-the-completion-source"></a>Реализация источника завершения  
 Источник завершения отвечает за сбор набора идентификаторов и добавление содержимого в окно завершения, когда пользователь вводит триггер завершения, например первые буквы идентификатора. В этом примере идентификаторы и их описания жестко запрограммированы в <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> методе. В большинстве реальных целей используется средство синтаксического анализа вашего языка, чтобы получить токены для заполнения списка завершения.  
  
#### <a name="to-implement-the-completion-source"></a>Реализация источника завершения  
  
1. Добавьте файл класса с именем `TestCompletionSource`.  
  
2. Добавьте следующие импорты:  
  
     [!code-csharp[VSSDKCompletionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#1)]
     [!code-vb[VSSDKCompletionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#1)]  
  
3. Измените объявление класса для `TestCompletionSource` так, чтобы оно реализовало <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> :  
  
     [!code-csharp[VSSDKCompletionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#2)]
     [!code-vb[VSSDKCompletionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#2)]  
  
4. Добавьте закрытые поля для поставщика источника, текстового буфера и списка <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> объектов (которые соответствуют идентификаторам, которые будут участвовать в сеансе завершения):  
  
     [!code-csharp[VSSDKCompletionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#3)]
     [!code-vb[VSSDKCompletionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#3)]  
  
5. Добавьте конструктор, который задает поставщик источника и буфер. `TestCompletionSourceProvider`Класс определяется в последующих шагах:  
  
     [!code-csharp[VSSDKCompletionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#4)]
     [!code-vb[VSSDKCompletionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#4)]  
  
6. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> метод, добавив набор завершения, содержащий завершения, которые необходимо предоставить в контексте. Каждый набор завершения содержит набор <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> завершений и соответствует вкладке окна завершения. (В Visual Basic проектах вкладки окна завершения именуются как **Общие** и **все**.) Метод Финдтокенспанатпоситион определяется на следующем шаге.  
  
     [!code-csharp[VSSDKCompletionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#5)]
     [!code-vb[VSSDKCompletionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#5)]  
  
7. Следующий метод используется для поиска текущего слова в позиции курсора:  
  
     [!code-csharp[VSSDKCompletionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#6)]
     [!code-vb[VSSDKCompletionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#6)]  
  
8. Реализуйте `Dispose()` метод:  
  
     [!code-csharp[VSSDKCompletionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#7)]
     [!code-vb[VSSDKCompletionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#7)]  
  
## <a name="implementing-the-completion-source-provider"></a>Реализация поставщика источника завершения  
 Поставщик источника завершения — это часть компонента MEF, которая создает экземпляр источника завершения.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Реализация поставщика источника завершения  
  
1. Добавьте класс с именем `TestCompletionSourceProvider` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> . Экспортируйте этот класс с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "обычным текстом" и <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "завершением теста".  
  
     [!code-csharp[VSSDKCompletionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#8)]
     [!code-vb[VSSDKCompletionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#8)]  
  
2. Импортируйте объект <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , который используется для поиска текущего слова в источнике завершения.  
  
     [!code-csharp[VSSDKCompletionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#9)]
     [!code-vb[VSSDKCompletionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#9)]  
  
3. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> метод для создания экземпляра источника завершения.  
  
     [!code-csharp[VSSDKCompletionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#10)]
     [!code-vb[VSSDKCompletionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#10)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Реализация поставщика обработчика команд завершения  
 Поставщик обработчика команд завершения является производным от класса <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , который прослушивает событие создания текстового представления и преобразует его из элемента <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> , который позволяет добавить команду в цепочку команд Visual Studio Shell в <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Поскольку этот класс является экспортом MEF, его также можно использовать для импорта служб, необходимых обработчику команды.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Реализация поставщика обработчика команд завершения  
  
1. Добавьте файл с именем `TestCompletionCommandHandler` .  
  
2. Добавьте следующие операторы using:  
  
     [!code-csharp[VSSDKCompletionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#11)]
     [!code-vb[VSSDKCompletionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#11)]  
  
3. Добавьте класс с именем `TestCompletionHandlerProvider` , реализующий <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Экспортируйте этот класс с помощью <xref:Microsoft.VisualStudio.Utilities.NameAttribute> обработчика завершения токенов, типа <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "обычный текст" и <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> объекта <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> .  
  
     [!code-csharp[VSSDKCompletionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#12)]
     [!code-vb[VSSDKCompletionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#12)]  
  
4. Импортируйте объект <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , который обеспечивает преобразование из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> в <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , и, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> а также <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> предоставляет доступ к стандартным службам Visual Studio.  
  
     [!code-csharp[VSSDKCompletionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#13)]
     [!code-vb[VSSDKCompletionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#13)]  
  
5. Реализуйте <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> метод для создания экземпляра обработчика команд.  
  
     [!code-csharp[VSSDKCompletionTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#14)]
     [!code-vb[VSSDKCompletionTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#14)]  
  
## <a name="implementing-the-completion-command-handler"></a>Реализация обработчика команд завершения  
 Поскольку завершение операторов активируется нажатиями клавиш, необходимо реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс для получения и обработки нажатий клавиш, которые инициируют, фиксируют и отменяют сеанс завершения.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Реализация обработчика команд завершения  
  
1. Добавьте класс с именем `TestCompletionCommandHandler` , реализующий <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :  
  
    [!code-csharp[VSSDKCompletionTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#15)]
    [!code-vb[VSSDKCompletionTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#15)]  
  
2. Добавьте закрытые поля для следующего обработчика команды (для передачи команды), представления текста, поставщика обработчика команд (который обеспечивает доступ к различным службам) и сеанса завершения:  
  
    [!code-csharp[VSSDKCompletionTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#16)]
    [!code-vb[VSSDKCompletionTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#16)]  
  
3. Добавьте конструктор, который задает поля "текстовое представление" и "поставщик", и добавляет команду в цепочку команд:  
  
    [!code-csharp[VSSDKCompletionTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#17)]
    [!code-vb[VSSDKCompletionTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#17)]  
  
4. Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод, передав команду:  
  
    [!code-csharp[VSSDKCompletionTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#18)]
    [!code-vb[VSSDKCompletionTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#18)]  
  
5. Выполните метод <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Когда этот метод получает нажатие клавиши, он должен выполнить одно из следующих действий:  
  
   - Разрешить запись символа в буфер, а затем запустить или завершить фильтрацию. (Печать символов.)  
  
   - Зафиксируйте завершение, но не разрешите запись символа в буфер. (Пробел, TAB и Enter это сделать при отображении сеанса завершения.)  
  
   - Разрешить передачу команды следующему обработчику. (Все остальные команды.)  
  
     Поскольку этот метод может отображать пользовательский интерфейс, вызовите, <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> чтобы убедиться, что он не вызывается в контексте автоматизации:  
  
     [!code-csharp[VSSDKCompletionTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#19)]
     [!code-vb[VSSDKCompletionTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#19)]  
  
6. Этот код является закрытым методом, который запускает сеанс завершения:  
  
    [!code-csharp[VSSDKCompletionTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#20)]
    [!code-vb[VSSDKCompletionTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#20)]  
  
7. Следующий пример является закрытым методом, который отменяет подписывание на <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> событие:  
  
    [!code-csharp[VSSDKCompletionTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#21)]
    [!code-vb[VSSDKCompletionTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#21)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы протестировать этот код, создайте решение Комплетионтест и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Создание и тестирование решения Комплетионтест  
  
1. Создайте решение.  
  
2. При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3. Создайте текстовый файл и введите текст, содержащий слово "Добавить".  
  
4. При вводе первого "a" и затем "d" должен отобразиться список, содержащий "Сложение" и "Адаптация". Обратите внимание, что выбрано сложение. При вводе другого "d" список должен содержать только "Сложение", которое теперь выбрано. Можно применить "Сложение", нажав клавиши пробел, TAB или клавишу ВВОД или отклонить список, введя ESC или любой другой ключ.  
  
## <a name="see-also"></a>См. также:  
 [Пошаговое руководство. Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
