---
title: "Пошаговое руководство: Отображение завершение операторов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d9c3b44bd46c34a864896cbf1002505085be5143
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-statement-completion"></a>Пошаговое руководство: Отображение завершение операторов
Завершение операторов, основанный на языке можно реализовать путем определения идентификаторов, для которых вы хотите предоставить завершения и затем запуская процесс завершения сеанса. Можно определить завершение операторов в контекст языковой службы, определите расширение имени файла и тип содержимого и отображения завершение только этот тип или вы можете активировать завершения для существующих типов — например, «обычный текст». В этом пошаговом руководстве показано, как активировать завершение операторов для типа содержимого «обычный текст», который является типом содержимого текстовых файлов. Тип содержимого «text» является предком всех других типов содержимого, включая код и XML-файлов.  
  
 Завершение операторов, обычно запускается, введя некоторые символы, например, введя в начале идентификатора, такого как «использование». Обычно оно закрывается, нажав клавишу ПРОБЕЛ, Tab или ввод для фиксации выделения. Можно реализовать функций IntelliSense, которые активируются, введя символ с помощью клавиш обработчика команд ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса) и поставщика обработчик, который реализует <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> интерфейса. Для создания источника завершения, который представляет собой список идентификаторов, которые участвуют в завершение, реализовать <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> интерфейс и поставщик завершения ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> интерфейс). Поставщики, компоненты Managed Extensibility Framework (MEF). Они отвечают за экспортирование классов источника и контроллера и импорта служб и брокеров — к примеру, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, позволяющий навигации в буфере и <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, которое запускает сеанс завершения.  
  
 В этом пошаговом руководстве показано, как реализовать завершение операторов с жестко набор идентификаторов. В полной реализации языковой службы и документация по языку несут ответственность за предоставление этого содержимого.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
#### <a name="to-create-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалогового окна выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Присвойте решению имя `CompletionTest`.  
  
2.  Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создания расширения с помощью шаблона элемента редактор](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
4.  Добавьте следующие ссылки в проект и убедитесь, что **CopyLocal** равно `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-the-completion-source"></a>Реализация источника завершения  
 Источник выполнения отвечает за сбор набор идентификаторов и добавление содержимого окна завершения, когда пользователь вводит завершения триггера, например первые буквы имени идентификатора. В этом примере идентификаторы и их описания жестко запрограммированы в <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> метод. В большинстве случаев реального мира используется средство синтаксического анализа языка для получения маркеров для заполнения списка завершения.  
  
#### <a name="to-implement-the-completion-source"></a>Для реализации источника завершения  
  
1.  Добавьте файл класса и назовите его `TestCompletionSource`.  
  
2.  Добавьте следующие импорты:  
  
     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  Измените объявление класса для `TestCompletionSource` , чтобы он реализовал <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  Добавьте закрытые поля для поставщика источника, буфер текста и список <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> объектов (которые соответствуют идентификаторы, которые будут участвовать в сеанс завершения):  
  
     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  Добавьте конструктор, который задает поставщик источника и буфера. `TestCompletionSourceProvider` Определения класса на последующих этапах:  
  
     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> метод путем добавления завершения набор, содержащий завершения требуется предоставить в контексте. Каждый набор завершения содержит набор <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> завершений и соответствует вкладке окна завершения. (В проектах Visual Basic с именем вкладки окна завершения **Общие** и **все**.) Метод FindTokenSpanAtPosition определен на следующем шаге.  
  
     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  Следующий метод используется для поиска текущего слова, начиная с позиции курсора:  
  
     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  Реализуйте `Dispose()` метод:  
  
     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## <a name="implementing-the-completion-source-provider"></a>Реализация поставщика источника завершения  
 Поставщик источника завершения — часть компонентов MEF, которая создает экземпляр источника завершения.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Для реализации поставщика источника завершения  
  
1.  Добавьте класс с именем `TestCompletionSourceProvider` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Экспортировать класс с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текста» и <xref:Microsoft.VisualStudio.Utilities.NameAttribute> «завершения тестирования».  
  
     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  Импорт <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, который используется для поиска в источнике завершения текущего слова.  
  
     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> метод для создания источника завершения.  
  
     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Реализация поставщика обработчик завершения команды  
 Поставщик обработчик завершения команды является производным от <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, который прослушивает событие создания представления текста и преобразует представление из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>— которой позволяет добавлять команды в цепочке командной оболочке Visual Studio — для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Поскольку этот класс является экспорта MEF, его можно также использовать для импорта службы, которые требуются, сам обработчик команды.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Для реализации поставщика обработчик завершения команды  
  
1.  Добавьте в файл с именем `TestCompletionCommandHandler`.  
  
2.  Добавьте следующие операторы using:  
  
     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  Добавьте класс с именем `TestCompletionHandlerProvider` , реализующий <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Экспорт этого класса с <xref:Microsoft.VisualStudio.Utilities.NameAttribute> «маркера завершения обработчика», <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текста» и <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> из <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  Импорт <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, который включает преобразование из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>и <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> , разрешающий доступ к стандартным службам Visual Studio.  
  
     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  Реализуйте <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> метод для создания обработчика команд.  
  
     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## <a name="implementing-the-completion-command-handler"></a>Реализация обработчика завершения команды  
 Поскольку завершение операторов реализована путем нажатия клавиш, необходимо реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс для получения и обработки нажатия клавиш, запускать, фиксировать и закрыть сеанс завершения.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Чтобы реализовать обработчик завершения команды  
  
1.  Добавьте класс с именем `TestCompletionCommandHandler` , реализующий <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
     [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
     [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2.  Добавьте закрытые поля, следующий обработчик команд (для которого передается команды), представления текста, поставщик обработчика команд (который предоставляет доступ к различным службам), а для завершения сеанса:  
  
     [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
     [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3.  Добавьте конструктор, который задает представления текста и полей поставщика и добавляет команду цепочки команды:  
  
     [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
     [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4.  Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод путем передачи команды вместе:  
  
     [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
     [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5.  Выполните метод <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Когда этот метод получает нажатие клавиши, необходимо выполнить одно из следующих действий:  
  
    -   Разрешение символов для записи в буфер и последующего инициирования или фильтрации завершения. (Печать символов это сделать).  
  
    -   Зафиксировать завершения, но не разрешать символ, записываемый в буфер. (Пробела, табуляции, а также ввод это сделать при отображении сеанс завершения).  
  
    -   Разрешить команду для передачи следующий обработчик. (Все другие команды.)  
  
     Поскольку этот метод может отображать пользовательский Интерфейс, вызывать <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> чтобы убедиться в том, что он не вызывается в контексте автоматизации:  
  
     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6.  Этот код представляет закрытый метод, который инициирует сеанс завершения:  
  
     [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
     [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7.  В следующем примере выполняются частного метода, который отменяет подписку <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> событий:  
  
     [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
     [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы проверить код, выполните сборку решения CompletionTest и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Для построения и тестирования решения CompletionTest  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создайте текстовый файл и введите текст, который содержит слово «добавить».  
  
4.  При вводе сначала «a» и затем «d», должен отображаться список, содержащий «сложение» и «адаптации». Обратите внимание, что выбран сложения. При вводе другой «d», список должен содержать только «сложение», что выбранное сейчас. Можно зафиксировать «Добавление», нажав клавишу ПРОБЕЛ, Tab или ввод или закрыть список, введя Esc или любую другую клавишу.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)