---
title: Пошаговое руководство. Отображение завершения операторов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c91f9aec4bd3db9a9495b2a05ce5153bf45f2f52
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009769"
---
# <a name="walkthrough-display-statement-completion"></a>Пошаговое руководство. Отображение завершения операторов
Завершение операторов на основе языка можно реализовать путем определения идентификаторов, для которых вы хотите предоставить завершения и затем активировать сеанс завершения. Можно определить завершение операторов в контексте языковой службы, определите расширение имени файла и тип содержимого и затем отобразить завершение только этого типа. Или вы можете активировать завершение существующий тип контента, например, «обычный текст». В этом пошаговом руководстве показано, как требуется активировать завершение операторов для типа содержимого «обычный текст», который является типом содержимого текстовых файлов. Тип содержимого «text» является предком всех других типов содержимого, включая код и XML-файлы.  
  
 Завершение операторов обычно запускается вводя некоторые символы, например, введя начале идентификатора, такого как «использование». Оно обычно закрывается, нажав клавишу **пробел**, **вкладке**, или **ввод** клавишу, чтобы зафиксировать выделения. Можно реализовать функции IntelliSense, которые активируют при вводе символа с помощью обработчика команды клавиш ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс) и поставщика обработчик, который реализует <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> интерфейс. Для создания источника завершения, которая является список идентификаторов, которые участвуют в завершении, реализовать <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> интерфейс и версиями завершения ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> интерфейс). Поставщики являются составные части Managed Extensibility Framework (MEF). Они отвечают экспортирование классов источника и контроллера и импорта служб и брокеров — к примеру, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, который позволяет осуществлять переходы в текстовом буфере и <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, что инициирует сеанс завершения.  
  
 В этом пошаговом руководстве показано, как реализовать завершение операторов с жестко набор идентификаторов. В полной реализации языковой службы и документацию по языку несут ответственность за предоставление этого содержимого.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не устанавливайте Visual Studio SDK в центре загрузки. Этот пакет включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Создание проекта MEF  
  
#### <a name="to-create-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалоговом окне выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Назовите решение `CompletionTest`.  
  
2.  Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
4.  Добавьте следующие ссылки в проект и убедитесь, что **CopyLocal** присваивается `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implement-the-completion-source"></a>Реализация источника завершения  
 Источник завершения отвечает за сбор набор идентификаторов и добавления содержимого в окне завершения, когда пользователь вводит триггер завершения, например первые буквы идентификатора. В этом примере, идентификаторы и их описания жестко запрограммированы в <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> метод. В большинстве случаев реального мира используется средство синтаксического анализа языка для получения маркеров для заполнения списка завершения.  
  
### <a name="to-implement-the-completion-source"></a>Для реализации источник завершения  
  
1.  Добавьте файл класса с именем `TestCompletionSource`.  
  
2.  Добавьте эти объекты импорта:  
  
     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  Измените объявление класса для `TestCompletionSource` таким образом, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  Добавьте закрытые поля для поставщика источника, текстовый буфер и список <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> объектов (соответствующие идентификаторы, которые будут участвовать в сеанс завершения):  
  
     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  Добавьте конструктор, который задает поставщик источника и буфера. `TestCompletionSourceProvider` Класс определен в следующих шагах:  
  
     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> метод путем добавления набора завершений, который содержит завершения требуется предоставить в контексте. Каждый набор завершения содержит набор <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> завершений и соответствует вкладке окна завершения. (В проектах Visual Basic, имеют имена вкладкам окна завершения **распространенных** и **все**.) Метод `FindTokenSpanAtPosition` определяется на следующем шаге.  
  
     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  Следующий метод используется для поиска текущего слова начиная с позиции курсора:  
  
     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  Реализуйте `Dispose()` метод:  
  
     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## <a name="implement-the-completion-source-provider"></a>Реализация поставщика источника завершения  
 Поставщик источника завершения — это часть компонентов MEF, которая создает экземпляр источника завершения.  
  
### <a name="to-implement-the-completion-source-provider"></a>Реализация поставщика источника завершения  
  
1.  Добавьте класс с именем `TestCompletionSourceProvider` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Экспорт этого класса с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текста» и <xref:Microsoft.VisualStudio.Utilities.NameAttribute> «завершения теста».  
  
     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  Импорт <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, которое выполняет поиск текущего слова в источник завершения.  
  
     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> метод для создания экземпляра источника завершения.  
  
     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## <a name="implement-the-completion-command-handler-provider"></a>Реализация поставщика обработчик завершения команды  
 Поставщиком обработчик завершения команд является производным от <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, который прослушивает событие создания представления текста и преобразует это представление из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>— который позволяет добавлять команды в цепочке командной оболочки Visual Studio — для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Так как этот класс является экспорт MEF, вы также можно использовать в импорте служб, которые требуются сам обработчик команды.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Реализация поставщика обработчик завершения команды  
  
1.  Добавьте в файл с именем `TestCompletionCommandHandler`.  
  
2.  Добавьте следующие операторы using:  
  
     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  Добавьте класс с именем `TestCompletionHandlerProvider` , реализующий <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Экспорт этого класса с <xref:Microsoft.VisualStudio.Utilities.NameAttribute> «обработчика маркера завершения», <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текста» и <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> из <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  Импорт <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, который включает преобразование из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>и <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> , разрешающий доступ к стандартным службам Visual Studio.  
  
     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  Реализуйте <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> метод для создания экземпляра обработчика команды.  
  
     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## <a name="implement-the-completion-command-handler"></a>Реализуйте обработчик завершения команды  
 Поскольку завершение операторов запускается нажатиями клавиш, необходимо реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс для получения и обработки нажатий клавиш, запуска, завершения и закрыть сеанс завершения.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Чтобы реализовать обработчик завершения команды  
  
1. Добавьте класс с именем `TestCompletionCommandHandler` , реализующий <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2. Добавьте закрытые поля для следующий обработчик команд (к которому передать команду), представление текста, поставщиком обработчик команд (который позволяет получать доступ к различным службам) и сеанс завершения:  
  
    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3. Добавьте конструктор, который задает представления текста и поля поставщика и добавляет команду в цепочку команды:  
  
    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4. Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод, передав команды вместе:  
  
    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5. Выполните метод <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Когда этот метод получает нажатие клавиши, он должен выполнить одно из этих вещей:  
  
   - Разрешить символ для записи в буфер и затем активировать или фильтрации завершения. (Печать символов для этого.)  
  
   - Фиксировать завершение, но не разрешать символ, записываемый в буфер. (Пробелы, **вкладке**, и **ввод** это сделать, если сеанс завершения отображается.)  
  
   - Разрешить команда передается следующий обработчик. (Все другие команды.)  
  
     Так как этот метод может отобразить пользовательский Интерфейс, вызывать <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> чтобы убедиться в том, что он не вызывается в контексте службы автоматизации:  
  
     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6. Этот код — это закрытый метод, который запускает сеанс завершения:  
  
    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7. В следующем примере выполняются закрытый метод, который отменяет подписку <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> событий:  
  
    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## <a name="build-and-test-the-code"></a>Построение и тестирование кода  
 Чтобы протестировать этот код, выполните сборку решения CompletionTest и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Построение и тестирование решения CompletionTest  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике, запускается второй экземпляр Visual Studio.  
  
3.  Создайте текстовый файл и введите текст, который включает слово «добавить».  
  
4.  При вводе сначала «a» и затем «d», появится список, содержащий «сложение» и «адаптации». Обратите внимание на то, что выбран сложения. При вводе другой «d», этот список должен содержать только «дополнение», который теперь можно выбрать. Вы можете фиксировать «дополнение», нажав клавишу **пробел**, **вкладке**, или **ввод** ключа, либо закрыть список, введя Esc или любую другую клавишу.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)